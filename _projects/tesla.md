---
layout: page
title: DNN Battery Safety
description: Leveraging On-Board Sensor Data for Abuse Mode Identification via DNNs and Random Forests
img: assets/tesla/3 slide summary of work.jpg
importance: 1
category: Work Experience
---

<!-- Project Title -->
<h1 style="font-size: 1.5em; font-weight: bold;">Enhancing Battery Safety: Leveraging On-Board Sensor Data for Abuse Mode Identification via DNNs and Random Forests
</h1>
<!-- Project Title -->

<!-- Subheading -->
<h2 style="font-size: 1.2em; font-style: italic; margin-top: 1.5em;">Background and Motivation</h2>
<!-- Subheading -->

<p style="margin-top: 0.3em;">
    Given the architecture of battery powered electric vehicles, namely the placement of the Lithium Ion battery below the floor of the car, damage to the battery due to road debris, rash driving, and crashes is a major concern for EV companies. Although EV car design has evolved to a point where only 25.1 out of 100,000 of EVs sold catch fire in a year [1], which is considerably less than ICE (Internal Combustion Engine) powered vehicles, many fires are prevented due to strategic recalls of fire prone vehicles by EV companies. According to data from the data processed from government sources [2], in 2020 alone, over 150,000 EVs were recalled from the field due to suspected battery damage which made the cars a fire risk. Moreover, given the fact that battery fires burn hotter and release more toxic fumes [3] than ICE vehicle fires, the timely detection and prevention of fatal battery damage becomes an important field of study to be undertaken by EV companies. <br><br>

    With the advent of autopilot and driving assistant systems, car companies now have more data than ever at their disposal about driving habits, common field issues, and driving edge cases. My project aims to leverage this data in order to create a prediction algorithm that firstly classifies possible battery damage cases by severity of damage- and further hopes to identify the exact location and energy of impact to the battery pack. The accurate classification of battery damage helps inform true incident rates, such that if a certain architecture is more prone to battery damage, or a certain type of battery damage is increasingly seen in the field, it can be flagged and designed for. I have used a combination of pre-data processing to create the most informative dataset with the largest signal between different battery damage categories, as well as a Deep Neural Network (DNN) algorithm for the actual prediction of damage.


</p>

<div class="row text-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/geckobot/gb_fig1.png" title="Figure 1" class="img-fluid rounded" width="100%" height="auto" %}
    </div>
</div>

<p style="margin-top: 0.3em;">
    Figure 1-i illustrates the forces acting on a single spatula when the gecko is adhered to the wall. The lateral friction force \( F_L \) and normal adhesion force \( F_N \) act on each spatula during adhesion. Furthermore, the angle that varies the net force acting on each spatula, \( F(\theta) \), is often less than 45°. Therefore, the lateral friction force that acts on the spatula contributes non-negligibly to the gecko’s ability to not slip against the wall. The equation for \( F(\theta) \) is:
</p>

<div class="row text-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/geckobot/gb_fig2.png" title="Figure 2" class="img-fluid rounded" width="300" height="auto" %}
    </div>
</div>

<p style="margin-top: 0.3em;">
    Researchers have employed MENS/NENS fabrication techniques, including photolithography, micro-molding, and plasma etching to manufacture pads with structures that emulate geckos’ setae [2,3].
</p>

<!-- Subheading -->
<h2 style="font-size: 1.2em; font-style: italic; margin-top: 1.5em;">Design Discussion</h2>
<!-- Subheading -->

<p style="margin-top: 0.3em;">
    We began the project by designing a locomoting robot that could emulate the gecko’s locomotive climbing cycle and avoid pitch-back as it climbs up a wall. The robot would have four legs, and each leg had two degrees of freedom to replicate a gecko’s limb. One degree of freedom allowed abduction and adduction of each leg for the robot to move forward and lift itself up the surface. The other degree of freedom provided flexion and extension of each leg allowing the robot to adhere to and peel away from the wall. We chose to use eight servos to drive these movements because of their ability to precisely control the rotation of their motor shaft. The maximum mass of the robot would be 0.7 kg (W ~ 7N). The body and legs were made out of PLA to minimize the robot’s weight.
</p>

<!-- Sub-Subheading -->
<h3 style="font-size: 1.05em; font-style: italic; margin-top: 1.5em;">Force Analysis for Servo Selection</h3>
<!-- Sub-Subheading -->

<p style="margin-top: 0.3em;">
    We carried out static force analysis to select the optimal dimensions of the robot and aid in motor selection. Since we planned on using 55g servos, we couldn’t neglect the weight of the linkages. Hence, we first found the equivalent CG of the entire robot in neutral position as such:
</p>

<div class="row text-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/geckobot/gb_fig5.png" title="Figure 3" class="img-fluid rounded" width="450" height="auto" %}
    </div>
</div>
<div class="caption text-center">Figure 2: FBD of Robot (Equivalent Weight and CG Marked)</div>

<div class="row text-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/geckobot/gb_fig4.png" title="Figure 4" class="img-fluid rounded" width="90%" height="auto" %}
    </div>
</div>

<p style="margin-top: 0.3em;">
    Since the robot is symmetric about the X axis, the Y coordinate of the CG can be found using CAD at 9cm from the back foot base. Thus, knowing the location of the CG in neutral position, we can label the minimum required adhesion and normal forces while the robot is in the "resting" position- all legs neutral, feet against a vertical surface. Seeing Fig [3], d1 is the distance between the robot’s center of mass and the wall, d2 is the distance between the CG and the middle of the first foot, and d3 is the distance between the centers of the two feet. Once again, only half of the robot weight is considered due to symmetry. Considering the robot to be in equilibrium at this moment, we find: 
</p>

<div class="row text-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/geckobot/gb_fig6.png" title="Figure 6" class="img-fluid rounded" width="270" height="auto" %}
    </div>
</div>

<p style="margin-top: 0.3em;">
    Moreover, since the robot is not slipping, the moments about the two feet centers and the CG balance out as: 
</p>

<div class="row text-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/geckobot/gb_fig7.png" title="Figure 7" class="img-fluid rounded" width="500" height="auto" %}
    </div>
</div>

<p style="margin-top: 0.3em;">
    From this moment balance, we see that:
</p>

<div class="row text-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/geckobot/gb_fig8.png" title="Figure 8" class="img-fluid rounded" width="185" height="auto" %}
    </div>
</div>

<p style="margin-top: 0.3em;">
    Equations (8) and (9) can also be found from the symmetry consideration of the robot. Finally, rearranging equation 7 yields the required horizontal force: 
</p>

<div class="row text-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/geckobot/gb_fig9.png" title="Figure 9" class="img-fluid rounded" width="230" height="auto" %}
    </div>
</div>

<p style="margin-top: 0.3em;">
    Given the designed values of d1, d2, and d3, we find the need for a horizontal force acting towards the surface of roughly 30% of the half weight of the robot. This is usually achieved in industry using vacuum suction cups. We also find the upwards shear forces on each pad to be 25% of the full robot weight, which is expected from the neutral position. Hence we find the resting torque required from each leg servo as T = FL, where L is the length of the linkage. For the foot servos, the torque can be easily found as Tf = GL, where L is again the length of the linkage and G is the weight of each foot in Newtons. 
</p>

<!-- Subheading -->
<h2 style="font-size: 1.2em; font-style: italic; margin-top: 1.5em;">Silicone Pad design and Adhesive force test</h2>
<!-- Subheading -->

<p style="margin-top: 0.3em;">
    Once we knew of the forces required from the servos, we moved on to finalize the form factor and design of the silicone pads. Our choice of silicone epoxy came from a previous project based on the research of Autumn et al[11] into synthetic materials that can mimic the unique properties of gecko feet. While conventional Pressure Sensitive Adhesives (PSAs) like duct tape or sticky note glue work on pure adhesion, the setae on gecko pads are an anisotropic frictional adhesive that require a proximally directed shear frictional force to maintain adhesion to the desired surface (Autumn et al, 2008). 
 
    Each gecko foot has over 200,000 setae per toe, each of which provide an adhesive force that is directionally dependent on the angle of contact between the setae and the surface of interest. To create our gecko inspired adhesive, we used a polydimethylsiloxane (PMDS) and initially tried to replicate the features of a lamella. We used acrylic laser cutting as a manufacturing method to create molds with various different shapes of lamellae cut out, including circles of varying diameters, flanges, and even molds with no lamellae. The objective was to measure the adhesive force of each design and finally implement the design providing the highest adhesive force. 
    
    In order to test the shear v/s adhesive force of each pad design, we planned to first adhere the pads to a vertical surface by providing a horizontal pushing force, and then begin attaching weights of increasing denominations to the pads and measure the maximum weight it was able to take without slipping. During the test, we realized the inefficiencies of our manufacturing methods- despite using the smallest allowable thickness settings of the laser cutter (0.1mm), the lamellae we created were too thick and were hence unable to bend as required to adhere to the vertical surface without the application of a significant horizontal force. Upon further research, we saw that lamellae used to replicate gecko adhesives have micron diameters, which we could not manufacture due a lack of microfabrication techniques. Moreover, the horizontal force would be in addition to that calculated in the previous section, and we realized that without additional mechanisms- like suction cups- it would be impossible for the robot to generate such high forces. In an attempt to reduce the weight and complexity of the project, we opted out of using additional force producing designs, and hence chose to forgo implementing lamellae and went with plain pads as they performed the best during adhesion testing. We also chose to modify the scope of the project to climb an inclined surface and measure the maximum incline the robot could climb without slipping, as climbing a perfectly vertical wall would be impossible without additional horizontal force. 
 
    During testing, we saw that each 2x2inch plain PMDS pad was capable of handling 170g at 71 degrees and 250g at 47 degrees without slipping. Since our robot was estimated to weigh ~715g, we expected our maximum incline to be 61 degrees from horizontal.
</p>

<!-- Subheading -->
<h2 style="font-size: 1.2em; font-style: italic; margin-top: 1.5em;">Robot’s Locomotive Cycle</h2>
<!-- Subheading -->

<p style="margin-top: 0.3em;">
    With resting servo forces calculated and silicone pad form factors decided, we moved on to creating the locomotive cycle of the robot that would then be implemented using the on board Arduino and a PWM servo controller. Each foot servo was used to lift feet off the ground and make ground contact, and the leg servos were used to swing the robot back and forth. Our locomotive cycle was based on the diagonal gait used by many researchers, which uses two diagonal legs to support the robot's body as it moves. In this gait, two diagonal legs extend forward and then pull the robot back, and by oscillating between the right diagonal and left diagonal legs, the robot lopes its way forward. This gait is inherently unstable because of the constant shift in CG due to the extension of only two legs at a time. Gecko's- and other industrial robots- overcome this CG shift by using CG correcting appendages like tails, and by fluidly twisting the torso to maintain CG along the path, as seen in the figures below. 
</p>

<div class="row text-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/geckobot/gb_fig10.png" title="Figure 10" class="img-fluid rounded" width="90%" height="auto" %}
    </div>
</div>

<div class="caption text-center">Figure 3: (Above) Diagonal Gait cycle of robot and (Below) twist and tail movement of Gecko during cycle (source Autumn et al, 2006 [11])</div>

<div class="row text-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/geckobot/gb_fig11.png" title="Figure 11" class="img-fluid rounded" width="80%" height="auto" %}
    </div>
</div>

<p style="margin-top: 0.3em;">
    We decided to slightly modify the diagonal gait by extending and pulling back all four legs of the robot at the same time, which would ensure that our CG did not shift away from our desired path. To confirm the stability of this gait we began by analyzing the CG shift and force on CG during regular motion. Assuming a limb length of L, and individual limb weights assigned sequentially, we see that in the neutral position, the Y coordinate of the CG can be found as: 
</p>

<div class="row text-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/geckobot/gb_fig12.png" title="Figure 12" class="img-fluid rounded" width="450" height="auto" %}
    </div>
</div>

<p style="margin-top: 0.3em;">
    Where theta is the angle with which the limb rotates. Hence we see that as each limb swings forward, the CG shifts slightly forward as well, but due to the symmetry of the robot there is no stray in the X direction. The motion of the gecko with the modified diagonal gait can be summarized as below. The Orange dots represent limb CG and the red dots represent past and present values of system CG.
</p>

<div class="row text-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/geckobot/gb_fig13.png" title="Figure 13" class="img-fluid rounded" width="450" height="auto" %}
    </div>
</div>
<div class="caption text-center">Figure 4: Robot Modified Diagonal Gait</div>

<!-- Subheading -->
<h2 style="font-size: 1.2em; font-style: italic; margin-top: 1.5em;">CAD Model of Design</h2>
<!-- Subheading -->

<p style="margin-top: 0.3em;">
    With all our calculations done, we created our first design iteration, which is shown in Figure 7. Taking the static force analysis conducted above into consideration, we connected the robot’s legs to the underside of its body to minimize the distance between its center of mass and the climbing surface. We also connected the servo for controlling the attachment/detachment of the foot closer to the foot so that less torque would need to be delivered to carry out this movement. The dimensions of the body were 7 inches long and 3 inches wide. The height of the robot’s legs, d1, was 2.5 inches and the length of each leg, d5, was 3.5 inches. The distance between the front and back legs, d23, was 4.5 inches.  
</p>

<div class="row text-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/geckobot/gb_fig14.png" title="Figure 14" class="img-fluid rounded" width="450" height="auto" %}
    </div>
</div>
<div class="caption text-center">Figure 5: CAD Model of the first design iteration.</div>

<!-- Subheading -->
<h2 style="font-size: 1.2em; font-style: italic; margin-top: 1.5em;">Final Design Iteration</h2>
<!-- Subheading -->

<p style="margin-top: 0.3em;">
    With the 55g servos, the last step remaining was to confirm that the supplied servo torque would be enough to drag the robot forward as seen in the robot locomotive cycle (see figure 6). For this, we performed a basic force analysis on the joints of the robot:
</p>
<div class="row text-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/geckobot/gb_fig15.png" title="Figure 15" class="img-fluid rounded" width="300" height="auto" %}
    </div>
</div>

<p style="margin-top: 0.3em;">
    Here Fa is the adhesive force, Fs is the backward force due to the moment M by the servo, and Ft is the net force pushing the body of the GeckoBot forward. For the robot to move, the force of adhesion must be exactly equal to the servo force, such that the pads don't move, which forces the main body to move instead. Assuming a limb length L, we see that:
</p>

<div class="row text-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/geckobot/gb_fig16.png" title="Figure 16" class="img-fluid rounded" width="450" height="auto" %}
    </div>
</div>

<p style="margin-top: 0.3em;">
    When the robot is perfectly horizontal. When the robot is on an incline of angle phi, then an additional W*sin(phi) component also acts in the downward direction, and the adhesive force must be modified as: 
</p>

<div class="row text-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/geckobot/gb_fig17.png" title="Figure 17" class="img-fluid rounded" width="230" height="auto" %}
    </div>
</div>

<p style="margin-top: 0.3em;">
    Since we did not implement lamellae, our adhesive force was angle independent as was estimated at a constant value based on physical testing. Hence, this constant adhesive force became a limiting factor in the maximum angle phi the robot could climb, and we found that the supplied servo torque was more than sufficient for efficient horizontal movement and measurement of inclined locomotion. Given the torque rating of 12 Kgcm at 6V for each of the leg servos, we found the net forward thrust force provided by all servos to be 4 times the system weight. Based on previous research, the average required forward force is 71% of body weight when climbing vertically [12], so having the large force margin was desirable as it allowed us to focus on the performance of the gecko inspired adhesive.
</p>

<!-- Subheading -->
<h2 style="font-size: 1.2em; font-style: italic; margin-top: 1.5em;">Results</h2>
<!-- Subheading -->

<p style="margin-top: 0.3em;">
    Tests were conducted on an inclined, clean white board. We initially took tests with the robot at rest and with all four of its feet on the white board to ensure the pads were sticky enough to adhere to inclined surfaces. It was determined that the robot could adhere to the white board at an average angle of 71.3°. After these initial tests, we conducted a series of five tests to find the maximum incline angle the robot could climb up without slipping and with slipping. The first five tests were conducted on Monday, November 28th and the last five tests were conducted on Tuesday, November 29th. We conducted these tests by placing the robot at the bottom of the whiteboard and letting it walk up the board for 10 seconds. We increased the incline angle by about 2 degrees until its maximum incline angle was reached.
</p>

<div class="row text-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/geckobot/gb_fig18.png" title="Figure 18" class="img-fluid rounded" width="450" height="auto" %}
    </div>
</div>
<div class="caption text-center">Figure 6: FBD of Robot (Equivalent Weight and CG Marked)</div>

<p style="margin-top: 0.3em;">
    As seen in the table below, the results aligned well with our predicted maximum angle phi. However, we did notice some slippage in the pads even at lower angles, and this was attributed to the manufacturing method of inconsistencies in mold setting and post processing.   
</p>

<div class="row text-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/geckobot/gb_fig19.png" title="Figure 19" class="img-fluid rounded" width="85%" height="auto" %}
    </div>
</div>

<!-- Subheading -->
<h2 style="font-size: 1.2em; font-style: italic; margin-top: 1.5em;">Future Improvements</h2>
<!-- Subheading -->

<p style="margin-top: 0.3em;">
    Figure (8) is the estimated gait cycle of our gecko bot and figure (9) is the gait cycle of a gecko according to researchers at the technical university of Hamburg. Comparing the two gait cycles, we can see that our gecko gait cycle initially has a similar trend compared to figure 8. However, the trend quickly becomes different. Our gait cycle explained that we attempted a different method for the locomotion of the gecko as we quickly discovered our limits such as manufacturing accuracy and weight limit would not allow for accurate mimic of gecko movement. 
</p>

<div class="row text-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/geckobot/gb_fig20.png" title="Figure 20" class="img-fluid rounded" width="85%" height="auto" %}
    </div>
</div>
<div class="caption text-center">Figure 7: Gait cycle according to UTH [8] v/s GeckoBot gait cycle</div>
