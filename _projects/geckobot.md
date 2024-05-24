---
layout: page
title: GeckoBot
description: Gecko and frog inspired 8DoF locomoting robot. Capable of climbing max 28 degree incline with no support.
img: assets/img/geckobot/geckobot_cover.png
importance: 2
category: work
giscus_comments: true
---

<!-- style="width: 400px; height: auto;" -->

<!-- Project Title -->
<h1 style="font-size: 1.5em; font-weight: bold;">GeckoBot: A Gecko Inspired Incline-Climbing Robot </h1>
<!-- Project Title -->

<p style="margin-top: 1.5em;">
    Vertical wall climbing robots have been a subject of scientific research for several years and could be used in a variety of applications. Robots that climb could eliminate the need for scaffolding when fulfilling jobs such as inspecting and maintaining airplanes and relieve humans of hazardous tasks such as window-washing and firefighting. An important consideration when designing these robots is its method for adhering to surfaces; consequently, researchers have identified and implemented different mechanisms for adhesion, including magnetic, pneumatic, electrostatic, and bio-inspired methods. Frequently, researchers have borrowed from the gecko’s unique method for adhesion when designing wall-climbing robots. Our project objective was to measure the effectiveness of a commonly used gecko-inspired adhesive in imparting wall climbing capabilities to a locomoting robot. Originally, we had planned to test our custom manufactured adhesive on a vertical wall- however, due to a lack of access to microfabrication techniques, we were forced to narrow our testing to inclined walls, and instead chose to measure the maximum incline our robot could climb without slipping thanks to the gecko-inspired adhesive feet.
</p>

<!-- Subheading -->
<h2 style="font-size: 1.2em; font-style: italic; margin-top: 1.5em;">Gecko’s Method for Adhesion</h2>
<!-- Subheading -->

<p style="margin-top: 0.3em;">
    The remarkable climbing ability of the gecko has been attributed primarily to the tiny, hair-like structures found on the toes. The toes hold modified keratinized scales called lamellae which are subdivided into tiny, hair-like structures called setae. These structures are composed of several nanoscale-sized spatulae which provide high adhesion and friction forces between the toe pads and surfaces through van der Waals forces [1]. Figure 1 shows the hierarchical structure of the gecko and the forces that act on its components.
</p>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/geckobot/gb_fig1.png" title="Figure 1" class="img-fluid rounded" %}
    </div>
</div>

<p style="margin-top: 0.3em;">
    Figure 1-i illustrates the forces acting on a single spatula when the gecko is adhered to the wall. The lateral friction force FLand normal adhesion force FN act on each spatula during adhesion. Furthermore, the angle that varies the net force acting on each spatula, F() is often less than 45°. Therefore, the lateral friction force that acts on the spatula contributes non negligible to the gecko’s ability to not slip against the wall. The equation for F(Theta) is:
</p>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/geckobot/gb_fig2.png" title="Figure 2"
        class="img-fluid rounded" 
        style="display: block; margin: auto; width: 300; height: auto;" %}
    </div>
</div>

<p style="margin-top: 0.3em;">
    Researchers have employed MENS/NENS fabrication techniques, including photolithography, micro-molding, and plasma etching to manufacture pads with structures that emulate geckos’ setae [2,3]. 
</p>

<!-- Subheading -->
<h2 style="font-size: 1.2em; font-style: italic; margin-top: 1.5em;">Design Discussion</h2>
<!-- Subheading -->

<p style="margin-top: 0.3em;">
    We began the project by designing a locomoting robot that could emulate the gecko’s locomotive climbing cycle and avoid pitch-back as it climbs up a wall. The robot would have four legs and each leg had two degrees of freedom to replicate a gecko’s limb. One degree of freedom allowed abduction and adduction of each leg for the robot to move forward and lift itself up the surface. The other degree of freedom provided flexion and extension of each leg allowing the robot to adhere to and peel away from the wall. We chose to use eight servos to drive these movements because of their ability to precisely control the rotation of their motor shaft. The maximum mass of the robot would be 0.7 kg (W ~ 7N). The body and legs were made out of PLA to minimize the robot’s weight.
</p>

<!-- Sub-Subheading -->
<h3 style="font-size: 1em; font-style: italic; margin-top: 1.5em;">Force Analysis for Servo Selection</h3>
<!-- Sub-Subheading -->

<p style="margin-top: 0.3em;">
    We carried out static force analysis to select the optimal dimensions of the robot and aid in motor selection. Since we planned on using 55g servos, we couldn’t neglect the weight of the linkages. Hence, we first found the equivalent CG of the entire robot in neutral position as such: 
</p>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/geckobot/gb_fig5.png" title="Figure 3" class="img-fluid rounded" %}
    </div>
</div>
<div class="caption">
    Figure 3: FBD of Robot (Equivalent Weight and CG Marked)
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/geckobot/gb_fig4.png" title="Figure 4" class="img-fluid rounded" %}
    </div>
</div>

<p style="margin-top: 0.3em;">
Since the robot is symmetric about the X axis, the Y coordinate of the CG can be found using CAD at 9cm from the back foot base. Thus, knowing the location of the CG in neutral position, we can label the minimum required adhesion and normal forces while the robot is in the "resting" position- all legs neutral, feet against a vertical surface.  
</p>


<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/1.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/3.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/5.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<!-- <div class="caption">
    Caption photos easily. On the left, a road goes through a tunnel. Middle, leaves artistically fall in a hipster photoshoot. Right, in another hipster photoshoot, a lumberjack grasps a handful of pine needles.
</div> -->


You can also put regular text between your rows of images.
Say you wanted to write a little bit about your project before you posted the rest of the images.
You describe how you toiled, sweated, _bled_ for your project, and then... you reveal its glory in the next row of images.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/6.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/11.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    You can also have artistically styled 2/3 + 1/3 images, like these.
</div>

The code is simple.
Just wrap your images with `<div class="col-sm">` and place them inside `<div class="row">` (read more about the <a href="https://getbootstrap.com/docs/4.4/layout/grid/">Bootstrap Grid</a> system).
To make images responsive, add `img-fluid` class to each; for rounded corners and shadows use `rounded` and `z-depth-1` classes.
Here's the code for the last row of images above:

{% raw %}

```html
<div class="row justify-content-sm-center">
  <div class="col-sm-8 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/6.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
  </div>
  <div class="col-sm-4 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/11.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
```

{% endraw %}
