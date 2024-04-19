---
layout: page
title: project 2
description: a project with a background image and giscus comments
img: assets/img/3.jpg
importance: 2
category: work
giscus_comments: true
---

The design and analysis of a mast of a blasthole drill rig takes a collective effort of 15 engineers, about 12 months to complete. This is an extremely expensive process and additionally, there is no fixed method to design the mast. In this project, I developed ‘Mast Analyzer’ , an end-to-end Machine Learning model that predicts whether the designed mast of a blasthole drill rig fails in any critical load cases. The design engineers enter the mast parameters and load characteristics as the input to their website, and if the mast is failing for any load case, the engineer can re-enter the parameters to fix the error.

There was no data available to begin with, so I performed FEA for 6 mast configurations for multiple critical load cases and collected the stress data along multiple critical locations. The dataset had all the relevant mast parameters such as width, depth, height, and all the load characteristics such as pulldown force, torque, cylinder force, and also the stress and deflection values that we obtained. A problem was that the number of data points were not enough and hence, I implemented upsampling techniques such as CTGAN and SMOTE to increase the number of data points. Once the dataset was ready, I leveraged a combination of traditional ML algorithms such as XGB and Random Forest to develop the model.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/proj_2_1.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Landing page of the website.
</div>

A separate model was developed for each load case, and the error of each model was less than 10%. Once all the models were developed, a new mast which was not considered while generating the dataset was taken. I performed FEA of the mast for all the critical load cases, and then used my ‘Mast Analyzer’. The difference in results were less than 2%. The ‘Mast Analyzer’ currently saves 40% in design time.

In conclusion, I developed an end-to-end ML model to solve a real-world engineering problem, and validated the model with a new mast. The website is currently hosted on the company’s secure Azure server.
