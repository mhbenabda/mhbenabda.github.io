---
layout: page
title: Blood Pressure Measurement Wearable
description: Master Thesis
img: assets/img/Deepview.jpg
importance: 1
category: work
related_publications: true
---

This thesis is currently still on-going and this page will be updated soon.


<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/Deepview.jpg" title="Deepview" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    System Overview
</div>

### Overview
There is an extensive amount of work in literature on designing different machine learning models for blood pressure measurement (BPM) using photoplethysmography (PPG), with very good results at first glace. The common way to do is to collect sensor data and corresponding labels from a medical grade device and train a neural net to map one to the other. Although well intentioned, existing papers don't mention the fact that the input signal from standrad PPG+ECG doen't contain enough information for predicting BPM. Additionally, existing models are non-generalizable due hardware sensitive datasets and lack of available data due to their medical nature. 

To solve this I'm building a low-power wearable platform with the heighst end analog-front-end (AFE) on the market for PPG and ECG to collect data all day long to achieve continuous BPM. Additionally, I'm trying to answer teh following research question:\n
* Can we embedd more features in the PPG signal, by using deep infrared wavelengths (beyond 1000nm) to predict BPM?

So far, I started by developping an experiment board to do sensor integration, explore different sensor designs on the optics side (LEDs and Photodiodes), and run RTOS the board. The next step is to start collecting and analysing the data to find teh optimal design. Finally, I will create a more compact version with a wearable format, generate a dataset, and test different machine learning models to answer my research question.