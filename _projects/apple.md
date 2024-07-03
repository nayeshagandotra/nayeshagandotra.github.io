---
layout: page
title: Display Product Design
description: Summer 2022 Intern project for MacPD @ Apple
img: assets/img/apple/apple1.jpg
importance: 2
category: Work Experience
---

<!-- Project Title -->
<h1 style="font-size: 1.5em; font-weight: bold;">Improved Sub-Component Design for Market Released External Display
</h1>
<!-- Project Title -->

<p style="margin-top: 0.3em;">
    During my summer internship at Apple, I worked with the MacPD team, and was tasked with redesigning a sub-component of a market released display system to meet updated architecture and safety requirements. In this page, I'll go into a little detail of the project and tools/skills used. 
</p>

<div class="row text-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/apple/apple2.png" title="A picture of me at Apple Park" class="img-fluid rounded" width="100%" height="auto" %}
    </div>
</div>

<!-- Subheading -->
<h2 style="font-size: 1.2em; font-style: italic; margin-top: 1.5em;">Problem Statement</h2>
<!-- Subheading -->

<p style="margin-top: 0.3em;">
    The root goal of my project was to propose design changes such that a future display product would meet the "tip" rule- that is, be safe from tipping over when placed on an inclined surface (such as a standing desk) and lightly disturbed. This rule was created both as a safety and aesthetic requirement, and while it was satisfied by the previous generation of displays, the performance related upgrades in the next generation meant that the distribution of weight had changed, and hence work needed to be done on the following fronts:
</p>

<div class="row text-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/apple/apple3.png" title="Figure 3" class="img-fluid rounded" width="100%" height="auto" %}
    </div>
</div>

<!-- Subheading -->
<h2 style="font-size: 1.2em; font-style: italic; margin-top: 1.5em;">Tools Used</h2>
<!-- Subheading -->

<p style="margin-top: 0.3em;">
    For verifying tip related theories and proposed design changes, I made use of the following tools:
</p>

<ol>
    <li><em>Center of Gravity Measurement System with custom fixtures </em>
    <div class="row text-center">
        <div class="col-sm mt-3 mt-md-0">
            {% include figure.liquid path="assets/img/apple/apple4.png" title="Figure 4" class="img-fluid rounded" width="100%" height="auto" %}
        </div>
    </div>
    This device has an associated visualiser that shows you precise CG location for the mass placed on it with very high fidelity. It proved very useful for calculating predicted weight shifts for a wide range of product options.
    </li>
    <li> <em>Digital Image Correlation Testing</em>
    <div class="row text-center">
        <div class="col-sm mt-3 mt-md-0">
            {% include figure.liquid path="assets/img/apple/apple5.gif" title="Figure 5" class="img-fluid rounded" width="100%" height="auto" %}
        </div>
    </div>
    This type of testing allows the user to detect very minute shifts and movements in deformable parts, and was great help in identifying a previously unknown mode of deformation in the target sub-component, which could then be quantified and designed for.</li>
    <li> <em>SiemensNX and Tolerance Analysis</em>
    Custom prototypes were designed using SiemensNX, and a tolerance analysis was conducted on them to ensure proper fit and use. An example of the types of tolerance stackups used is as follows: 
    <div class="row text-center">
        <div class="col-sm mt-3 mt-md-0">
            {% include figure.liquid path="assets/img/apple/apple6.png" title="Figure 6" class="img-fluid rounded" width="100%" height="auto" %}
        </div>
    </div>
</ol>


