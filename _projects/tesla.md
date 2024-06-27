---
layout: page
title: DNN Battery Safety
description: Leveraging On-Board Sensor Data for Abuse Mode Identification via DNNs and Random Forests
img: assets/img/tesla/3 slide summary of work-2.jpg
importance: 1
category: Work Experience
---

<!-- Project Title -->
<h1 style="font-size: 1.5em; font-weight: bold;">Enhancing Battery Safety: Leveraging On-Board Sensor Data for Abuse Mode Identification via DNNs and Random Forests
</h1>
<!-- Project Title -->

<p style="margin-top: 0.3em;">
    From August 2023 to May 2024, I worked in the Abuse and Functional Safety R&D team at Tesla. My work involved creating experiments and proposing design specifications for crucial safety components across Tesla products, including Cybertruck (for which I represented my team in launch critical hands on testing, and got this super cool picture taken in return). One of the projects I worked on was a long term study on using fleet data to enhance battery safety- particularly to quantify statistically and design to prevent damage due to road debris, uneven driving, etc- and that's the project I'll talk about in some detail here. Specifics about the exact data type, models, and results are omitted to maintain the company's policy.
</p>

<div class="row text-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/tesla/tesla4.png" title="Figure 1" class="img-fluid rounded" width="100%" height="auto" %}
    </div>
</div>

<!-- Subheading -->
<h2 style="font-size: 1.2em; font-style: italic; margin-top: 1.5em;">Background and Motivation</h2>
<!-- Subheading -->

<p style="margin-top: 0.3em;">
    Given the architecture of battery powered electric vehicles, namely the placement of the Lithium Ion battery below the floor of the car, damage to the battery due to road debris, rash driving, and crashes is a major concern for EV companies. Although EV car design has evolved to a point where only 25.1 out of 100,000 of EVs sold catch fire in a year [1], which is considerably less than ICE (Internal Combustion Engine) powered vehicles, many fires are prevented due to strategic recalls of fire prone vehicles by EV companies. According to data from the data processed from government sources [2], in 2020 alone, over 150,000 EVs were recalled from the field due to suspected battery damage which made the cars a fire risk. Moreover, given the fact that battery fires burn hotter and release more toxic fumes [3] than ICE vehicle fires, the timely detection and prevention of fatal battery damage becomes an important field of study to be undertaken by EV companies. <br><br>

    With the advent of autopilot and driving assistant systems, car companies now have more data than ever at their disposal about driving habits, common field issues, and driving edge cases. My project aims to leverage this data in order to create a prediction algorithm that firstly classifies possible battery damage cases by severity of damage- and further hopes to identify the exact location and energy of impact to the battery pack. The accurate classification of battery damage helps inform true incident rates, such that if a certain architecture is more prone to battery damage, or a certain type of battery damage is increasingly seen in the field, it can be flagged and designed for. With this in mind, the goals of the project were as follows:
</p>

<ul>
    <li>Create a dataset of fleet cases classified by battery damage</li>
    <li>Use on-board autopilot sensor data to identify patterns of battery abuse</li>
    <li>Suggest improved data collection algorithms to reduce rate of “blind spots” - aka incidents that are incorrectly not flagged as potential abuse risks</li>
</ul>

<div class="row text-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/tesla/keynote cad.jpg" title="Figure 1" class="img-fluid rounded" width="100%" height="auto" %}
    </div>
</div>
<div class="caption text-center">Figure 1: Placement of Lithium Ion battery in EV and X,Y,Z axis definition. Source: [4] </div>

<!-- Subheading -->
<h2 style="font-size: 1.2em; font-style: italic; margin-top: 1.5em;">Methodology</h2>
<!-- Subheading -->
<!-- Sub-Subheading -->
<h3 style="font-size: 1.05em; font-style: italic; margin-top: 1.5em;">Random Forests</h3>
<!-- Sub-Subheading -->

<p style="margin-top: 0.3em;">
    Once labeled data was collected, ~92 features were identified as potential high impact features- ones that showed the highest signal between different damage types. Then, random forests were used to classify the data, and then feature importance plots were used to finalize focus features that could be used to improve data collection and binning.
</p>

<div class="row text-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/tesla/tesla3.jpg" title="Figure 2" class="img-fluid rounded" width="500" height="auto" %}
    </div>
</div>


