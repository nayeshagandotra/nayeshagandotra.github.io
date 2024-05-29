---
layout: page
title: PokeCatch
description: Real Time tracking automated arcade game that plays itself
img: assets/img/pokecatch/lvjisuoy22434.jpeg
importance: 4
category: Robotics
---

<!-- Project Title -->
<h1 style="font-size: 1.5em; font-weight: bold;">PokeCatch: A User Friendly Real Time Arcade Game</h1>
<!-- Project Title -->

<p style="margin-top: 1.5em;">
    Often in microprocessor based mechanical systems, it is desirable- if not necessary- to have real time sensor data to inform actuator motion. However, if the system consists of too many peripherals, a traditional implementation can result in a significant time delay between data acquisition and peripheral control due to the sequential manner in which microprocessor logic is executed. In this project, we sought to eliminate this delay by implementing prioritized timer interrupts firing at a constant calculated frequency, which allowed us to realize fine control of microprocessor level multitasking, hence resulting in measurably improved real time sensor data acquisition. We believe the technique of using multitasking to drive better real time implementations has pertinent uses in developing robot-human teams and adaptive robots that can use real time information to inform robustness to disturbance. <br><br>
 
    This project was a part of ME135, the Design of Microprocessor Based mechanical Systems class, and ME102B, the senior design project class- both of which have a joint showcase at the end of the semester where children from bay area high schools are invited to browse college level engineering projects. Knowing this, we decided to create a fun automated arcade game with an associated user-friendly interface in order to educate the participating children about the real world use of microelectronics. The “PokeCatch” game consisted of a moving target- pokemon- on a timing belt actuated by a DC motor, as well as a potentiometer controlled projectile system which shot a ping pong ball. The game additionally supported two modes- “human” and “robot”. In the robot mode, the game would predict target location based on real time magnetic encoder data and calculate an optimized ball trajectory to perfectly capture the moving target. Thus by comparing the human and robot mode implementations we were able to demonstrate the benefits of using multitasking to inform better real time actuation. 
</p>

<!-- Subheading -->
<h2 style="font-size: 1.2em; font-style: italic; margin-top: 1.5em;">Infrastructure Used:</h2>
<!-- Subheading -->

<p style="margin-top: 0.3em;">
    Recognizing that most well-documented open source microcontrollers don’t support multitasking, we opted to use the PSoC6 BLE microcontroller and the associated embedded C based ModusToolbox IDE to implement our project. Details about the same can be found on the Cypress Semiconductors Website.
</p>


<!-- Subheading -->
<h2 style="font-size: 1.2em; font-style: italic; margin-top: 1.5em;">Implementation</h2>
<!-- Subheading -->

<!-- Sub-Subheading -->
<h3 style="font-size: 1.05em; font-style: italic; margin-top: 0.3em;">Tracking System</h3>
<!-- Sub-Subheading -->

<p style="margin-top: 0.3em;">
    The tracking system consisted of a timing belt, two pulleys, and a DC motor with an encoder. We decided on a preliminary 1.5m as the length of the tracking system, and 0.5m/s as the speed of the target as it moved across the track. Based on availability, we chose 3cm diameter timing belt pulleys, and planned on fixing the target to the timing belt using an appropriate magnet. Based on these figures, we found the required torque output from the DC motor as 2.5 microN/meter.
</p>

<p style="margin-top: 0.3em;">
    The maximum input voltage was set to 12 V. Based on our torque requirements we chose the 25GA-370 DC 12V Micro Gear Box Motor. Once the Motor was selected, we design mounts and the base for the system to rest on and went into fabrication to test our motor outputs. <br><br>

    To drive the motor we used the ModusToolbox Hardware Abstraction Layer Library (HAL)  to initialize multiple PWM signals. One was used as a “get data” timer interrupt, which polled the GPIO pin connected to the motor encoder every 25 milliseconds. Another PWM signal was sent to the DC motor to drive the clockwise and counter clockwise depending on when the encoder count indicated the end of the track. From initial encoder readings, we were able to create a map between the encoder count and the track. Finally, we simplified all of this calculation to represent a real time visualisation of the target on the tracking system on the user facing GUI:
</p>

<div class="row text-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/pokecatch/pc1.png" title="Figure 1" class="img-fluid rounded" width="100%%" height="auto" %}
    </div>
</div>
<div class="caption text-center">Figure 1: (Above)Unedited and (Below) User facing GUI with start, stop, and human functionalities</div>
<div class="row text-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/pokecatch/pc2.png" title="Figure 2" class="img-fluid rounded" width="100%%" height="auto" %}
    </div>
</div>

<!-- Subheading -->
<h2 style="font-size: 1.2em; font-style: italic; margin-top: 1.5em;">Use of Multitasking: </h2>
<!-- Subheading -->

<p style="margin-top: 0.3em;">
    On the PSoC6 side, we implemented three timer interrupts to complete the functionalities we required. These were the “get data” interrupt, the “shoot” interrupt, and the “reset” interrupt. Because acquiring encoder data was critical to all subsequent tasks, we placed the get data interrupt at the highest priority in order to collect real time data and store it in an appropriate buffer. This ensured that there would be no data lost during the functioning of the system, and the 100% accurate shooting of the target proved that hypothesis. We placed the “shoot” interrupt at the second priority, because after data acquisition the next critical task was launching the ball automatically in the robot mode. Knowing the fact that the system takes around 3 seconds after sending the “shoot” command to launch the ball, as well as by using simple projectile motion to model the path of the ball, we calculated the exact spots where the trigger command would be sent. We then found the optimum potentiometer values to map to the servo that would take the projectile system to where it needed to be to hit the Pokemon. The result of that was that every time the pokemon crossed a certain location along the track, the timer interrupt would call the “shoot()” function, which would make the launcher shoot a ball that hit the pokemon. Finally, we implemented the reset interrupt at the lowest priority to rewind the spring every five seconds. This interrupt was triggered every time the shoot button was triggered, and functioned as a five second countdown before shooting could be commanded again. The interrupt flag was set to false within the “stop game” function so that the timer would reset every time the game started. It was implemented to prevent the mechanical system from choking due to too many shoot commands sent its way.
</p>

<div class="row text-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/pokecatch/pc3.png" title="Figure 3" class="img-fluid rounded" width="100%%" height="auto" %}
    </div>
</div>

<p style="margin-top: 0.3em;">
    There were two more interrupts that we had used to enable multitasking. We configured two GPIO interrupts to shoot the ping pong ball when in “human” mode and another to detect if the Pokemon had been shot successfully. The GPIO interrupt that shot the ping pong ball was triggered during the rising edge of a button. The interrupt handler checked if “human” mode was on and, if “human” mode was on, it would shoot the ping pong ball and set the has_shot flag to true. This flag was used in conjunction with the timer interrupt used to “reset” the shooter to ensure that the user had enough time to reload the projectile system.  <br><br>
 
    The GPIO interrupt that detected if the Pokemon had been shot successfully used data from a laser sensor that set a pin to high when the laser had detected that the Pokemon was off of the tracking system. This would update the user’s score in the game. Both of these interrupts were set at the lowest priorities since they weren’t considered as “time critical” as other tasks. 
</p>

<!-- Subheading -->
<h2 style="font-size: 1.2em; font-style: italic; margin-top: 1.5em;">Results and Conclusion </h2>
<!-- Subheading -->

<p style="margin-top: 0.3em;">
    Upon visual observation of the GUI plotting of target location, we found virtually no delay between the mapping of the target and the target movement in real life thanks to the prioritization of data acquisition and transmission. Additionally, the implementation of a buffer enabled us to store all past sensor values, which ensured that no significant point would be lost which could result in erroneous shooting by the launcher. Thus, by observing the multitasking system we can confidently advocate the use of nested interrupts to drive faster real time tracking of live data. 
 
    At the end of it all, our game was highly enjoyed by the spectators, who set up a “high score” chart to compare human performance to robot performance. We are glad to have been able to work on a fun application of a highly important microcontroller concept and gain a depth of knowledge on controlling microcontroller based mechanical systems through this project.
</p>

<!-- Subheading -->
<h2 style="font-size: 1.2em; font-style: italic; margin-top: 1.5em;">Contributors </h2>
<!-- Subheading -->

<p style="margin-top: 0.3em;">
    Brittany Navailles and Nayesha Gandotra
</p>