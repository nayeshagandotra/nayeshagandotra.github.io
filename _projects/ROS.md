---
layout: page
title: ROS Conductor
description: Sawyer manipulator made to conduct to audio input using ROS
img: assets/img/12.jpg
importance: 3
category: work
related_publications: true
---

<!-- Project Title -->
<h1 style="font-size: 1.5em; font-weight: bold;">ROS Conductor: A Sawyer Robot Music Conductor</h1>
<!-- Project Title -->

<p style="margin-top: 1.5em;">
    In teams featuring extensive human-robot interaction, there may be inefficiencies in functioning due to operators being uncomfortable with their robotic counterparts. One way to reduce human stigma against robots is to make their motion more humanoid- smoother, more predictive, more adaptive- as has been done by Catie Cuan of Stanford University [1]. Inspired by Catie’s research, my team and I set out to choreograph humanoid motion in the one armed Sawyer robots available to us. We chose to work with the motion of a human orchestra conductor, as the right hand of the conductor, which showcases rhythm and beat changes, can be modeled with a one handed robot. The project uses image processing, audio processing, and kinematic path and velocity planning to drive the desired motion of the robot.
</p>

<!-- Subheading -->
<h2 style="font-size: 1.2em; font-style: italic; margin-top: 1.5em;">Infrastructure Used:</h2>
<!-- Subheading -->

<p style="margin-top: 0.3em;">
    For the robot, we used Intera’s Sawyer robot, which has one arm. The motion planning was done using ROS’ MoveIt functionality, and the audio input was a microphone processed using ROS’ audio_common library. 
</p>


<!-- Subheading -->
<h2 style="font-size: 1.2em; font-style: italic; margin-top: 1.5em;">Implementation</h2>
<!-- Subheading -->

<!-- Sub-Subheading -->
<h3 style="font-size: 1.05em; font-style: italic; margin-top: 1.5em;">Motion Planning</h3>
<!-- Sub-Subheading -->

<p style="margin-top: 0.3em;">
    In order to start working with a conductor’s motion, we first studied the role of a conductor in an orchestra. Thanks to A Complete Idiot’s Guide to Conducting [2], we found that the role of an orchestra conductor is twofold:
To start the performance and establish and maintain a clear and uniform tempo
To help the musical quality of the piece (dynamics, rhythm, expression, etc). 
On account of working with a one armed Sawyer robot, we decided to focus on the rhythm and tempo aspect of conducting, aiming to showcase common motions undertaken by the dominant hand of the conductor. We then looked into the trajectory of the conductor’s baton, and decided to implement two fixed paths recommended by the book for a 2/2 and 4/4 time signature: 
</p>

<div class="row text-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/ros/ros1.png" title="Figure 1" class="img-fluid rounded" width="450" height="auto" %}
    </div>
</div>
<div class="caption text-center">Figure 1: Chosen Trajectories for motion</div>

<p style="margin-top: 0.3em;">
    Moreover, we also found that conductors often vary the amplitude and elaborateness of the motion depending on the tempo of the song- higher tempo pieces usually see simpler motions to denote beats and lower tempo pieces can have highly involved beat showcases as seen in figure 1. While there was no official standard for the reduction in amplitude of motion depending on the tempo of the piece, we decided to create our own custom amplitude scaling factor:
</p>

<div class="row text-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/ros/ros2.png" title="Figure 2" class="img-fluid rounded" width="450" height="auto" %}
    </div>
</div>

<p style="margin-top: 0.3em;">
    Where A is the amplitude, or the distance between the topmost and bottom-most point of a downbeat motion, and BPM is the measured beats per minute of the audio input. We also decided to save multiple trajectories- one with a lot of stops and hand twists and a simpler one in order to switch trajectories depending on the measured BPM. <br><br>

    Once we had the desired trajectories in mind, it was important to become familiar with the workspace of the Sawyer robot. We began by testing our desired upper and lower limits by placing the robot in zero g mode and creating a function called tf_echo meant to mimic the built in ROS tf_echo function in order to get the translation between the stationary and tool frame of the robot.
</p>

<div class="row text-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/ros/ros3.png" title="Figure 3" class="img-fluid rounded" width="450" height="auto" %}
    </div>
</div>
<div class="caption text-center">Figure 2: Representation of Sawyer Robot and associated joints</div>

<p style="margin-top: 0.3em;">
    In order to compare the real time TF values to our own calculated values, we used the concept of homogeneous coordinates to find gst(0) from the {S} to the {T} frame. We know that:  
</p>

<div class="row text-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/ros/ros4.png" title="Figure 4" class="img-fluid rounded" width="450" height="auto" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/ros/ros5.png" title="Figure 5" class="img-fluid rounded" width="450" height="auto" %}
    </div>
</div>

<p style="margin-top: 0.3em;">
    Moreover, by echoing the robot/joint_states topic, we find the required values of q at the given instance of time: 
</p>

<div class="row text-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/ros/ros6.png" title="Figure 6" class="img-fluid rounded" width="450" height="auto" %}
    </div>
</div>

<p style="margin-top: 0.3em;">
    This allows us to find gst(0) as:
</p>

<div class="row text-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/ros/ros7.png" title="Figure 7" class="img-fluid rounded" width="450" height="auto" %}
    </div>
</div>

<p style="margin-top: 0.3em;">
    Applying the concept of forward kinematics, we see that 
</p>

<div class="row text-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/ros/ros8.png" title="Figure 8" class="img-fluid rounded" width="450" height="auto" %}
    </div>
</div>

<p style="margin-top: 0.3em;">
    Once again using the robot/joint_state topic of the sawyer robot, we find the necessary thetas and xis at each instance of time, which results in the required gst(theta) value which can then be used for forward and inverse kinematics. <br><br>
 
    The gst theta was then published onto a separate topic called tf_echo, and the rotation was represented as a quaternion using the 3D rotation to quaternion conversion: 
</p>

<div class="row text-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/ros/ros9.png" title="Figure 9" class="img-fluid rounded" width="450" height="auto" %}
    </div>
</div>

<p style="margin-top: 0.3em;">
    The final message published to tf_echo contained the translation between the {S} and {T} frame as a 3D coordinate and the orientation of the tool frame represented as a quaternion. <br><br>

    Once the tf_echo function was fleshed out, we could get live transformation functions between the end effector and the base of the robot. Then, placing the robot in zero g mode, we took the robot to the highest and lowest point of interest and measured the noted orientation and translation values. We found that the highest point was roughly at [-0.89, 0.835, 0.1] and the lowest point was at [-0.89, 0.2, 0.3]. The x, y, and z axes of the sawyer robot were defined by the blue, red, and green axes as follows:
</p>

<div class="row text-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/ros/ros10.png" title="Figure 10" class="img-fluid rounded" width="450" height="auto" %}
    </div>
</div>
<div class="caption text-center">Figure 3: Figure 3: Axes definition for the Sawyer robot</div>

<p style="margin-top: 0.3em;">
    With this information on the end effector position at time t, we went into openCV to extract trajectories from input images for the sawyer robot to follow. 
</p>

<!-- Subheading -->
<h2 style="font-size: 1.2em; font-style: italic; margin-top: 1.5em;">OpenCV and Trajectory Recognition:</h2>
<!-- Subheading -->

<p style="margin-top: 0.3em;">
    In order to extract points along the trajectory for the sawyer arm to follow, we decided to use python’s open camera vision module to process an input JPG image and output translation and rotation in terms of an array of Poses, where each Pose() consists of a translation and orientation. We began by dividing the trajectory into multiple pieces- increasing y direction and decreasing y direction to ease in the sorting of the image array and drawing out those pieces using paint to feed into the image processing node.
</p>

<div class="row text-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/ros/ros10.png" title="Figure 10" class="img-fluid rounded" width="450" height="auto" %}
    </div>
</div>
<div class="caption text-center">Figure 3: Figure 3: Axes definition for the Sawyer robot</div>