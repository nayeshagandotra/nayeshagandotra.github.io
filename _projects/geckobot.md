---
layout: page
title: GeckoBot
description: Gecko and frog inspired 8DoF locomoting robot. Capable of climbing max 28 degree incline with no support.
img: assets/img/geckobot/geckobot_cover.png
importance: 2
category: work
giscus_comments: true
---

<!-- Project Title -->
<h1 style="font-size: 1.5em; font-weight: bold;">GeckoBot: A Gecko Inspired Incline-Climbing Robot</h1>
<!-- Project Title -->

<p style="margin-top: 1.5em;">
    Vertical wall climbing robots have been a subject of scientific research for several years and could be used in a variety of applications. Robots that climb could eliminate the need for scaffolding when fulfilling jobs such as inspecting and maintaining airplanes and relieve humans of hazardous tasks such as window-washing and firefighting. An important consideration when designing these robots is its method for adhering to surfaces; consequently, researchers have identified and implemented different mechanisms for adhesion, including magnetic, pneumatic, electrostatic, and bio-inspired methods. Frequently, researchers have borrowed from the gecko’s unique method for adhesion when designing wall-climbing robots. Our project objective was to measure the effectiveness of a commonly used gecko-inspired adhesive in imparting wall climbing capabilities to a locomoting robot. Originally, we had planned to test our custom manufactured adhesive on a vertical wall; however, due to a lack of access to microfabrication techniques, we were forced to narrow our testing to inclined walls, and instead chose to measure the maximum incline our robot could climb without slipping thanks to the gecko-inspired adhesive feet.
</p>

<!-- Subheading -->
<h2 style="font-size: 1.2em; font-style: italic; margin-top: 1.5em;">Gecko’s Method for Adhesion</h2>
<!-- Subheading -->

<p style="margin-top: 0.3em;">
    The remarkable climbing ability of the gecko has been attributed primarily to the tiny, hair-like structures found on the toes. The toes hold modified keratinized scales called lamellae which are subdivided into tiny, hair-like structures called setae. These structures are composed of several nanoscale-sized spatulae which provide high adhesion and friction forces between the toe pads and surfaces through van der Waals forces [1]. Figure 1 shows the hierarchical structure of the gecko and the forces that act on its components.
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
<div class="caption text-center">Figure 3: FBD of Robot (Equivalent Weight and CG Marked)</div>

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
        {% include figure.liquid path="assets/img/geckobot/gb_fig6.png" title="Figure 6" class="img-fluid rounded" width="350" height="auto" %}
    </div>
</div>

<p style="margin-top: 0.3em;">
    Moreover, since the robot is not slipping, the moments about the two feet centers and the CG balance out as: 
</p>

<div class="row text-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/geckobot/gb_fig7.png" title="Figure 7" class="img-fluid rounded" width="350" height="auto" %}
    </div>
</div>

<p style="margin-top: 0.3em;">
    From this moment balance, we see that:
</p>

<div class="row text-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/geckobot/gb_fig8.png" title="Figure 8" class="img-fluid rounded" width="350" height="auto" %}
    </div>
</div>

<p style="margin-top: 0.3em;">
    Equations (8) and (9) can also be found from the symmetry consideration of the robot. Finally, rearranging equation 7 yields the required horizontal force: 
</p>

<div class="row text-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/geckobot/gb_fig9.png" title="Figure 9" class="img-fluid rounded" width="350" height="auto" %}
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


<!-- <div class="row text-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/1.jpg" title="example image" class="img-fluid rounded z-depth-1" width="200" height="auto" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/3.jpg" title="example image" class="img-fluid rounded z-depth-1" width="250" height="auto" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/5.jpg" title="example image" class="img-fluid rounded z-depth-1" width="300" height="auto" %}
    </div>
</div> -->

<p>
    You can also put regular text between your rows of images. Say you wanted to write a little bit about your project before you posted the rest of the images. You describe how you toiled, sweated, _bled_ for your project, and then... you reveal its glory in the next row of images.
</p>

<div class="row justify-content-sm-center text-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/6.jpg" title="example image" class="img-fluid rounded z-depth-1" width="500" height="auto" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/11.jpg" title="example image" class="img-fluid rounded z-depth-1" width="300" height="auto" %}
    </div>
</div>
<div class="caption text-center">
    You can also have artistically styled 2/3 + 1/3 images, like these.
</div>

The code is simple. Just wrap your images with `<div class="col-sm text-center">` and place them inside `<div class="row">` (read more about the <a href="https://getbootstrap.com/docs/4.4/layout/grid/">Bootstrap Grid</a> system). To make images responsive, add `img-fluid` class to each; for rounded corners and shadows use `rounded` and `z-depth-1` classes. Here's the code for the last row of images above:

{% raw %}

```html
<div class="row justify-content-sm-center text-center">
  <div class="col-sm-8 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/6.jpg" title="example image" class="img-fluid rounded z-depth-1" width="500" height="auto" %}
  </div>
  <div class="col-sm-4 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/11.jpg" title="example image" class="img-fluid rounded z-depth-1" width="300" height="auto" %}
  </div>
</div>
```

{% endraw %}