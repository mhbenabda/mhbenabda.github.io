---
layout: page
title: DeepView
description: "Master Thesis: Deep-Infrared Wearable for Continuous Blood Pressure Monitoring"
img: assets/img/p1_deepview.jpg
importance: 1
category: work
related_publications: false
---

This thesis is currently still on-going and this page will be updated soon.


<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/p1_deepview.jpg" title="Deepview" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    System Overview
</div>

## Overview


**The Challenge: Why Current ML-BPM Fails**

While literature is saturated with Machine Learning models for Blood Pressure Monitoring (BPM) using Photoplethysmography (PPG), most results are misleading and cannot be translated to the real-world. I have identified three critical bottlenecks in the current state-of-the-art:

1. **Information Scarcity:** Standard PPG and ECG signals don't contain enough information to predict blood pressure, making common approach foundamentally wrong.

2. **Dataset Sensitivity:** Existing models are frequently "overfit" to a specific hardware or to the public dataset used, making them non-generalizable across different sensors.

3. **Data Scarcity:** The medical nature of BP data leads to small, proprietary datasets that hinder deep learning progress. Additionally, existing data is overconstrained where data far from normal range is discarded as outliers or noise, which statistically simplifies the task, but limits model detecting abnormal cases.

#### My Approach: Deep-Infrared Sensing & Edge Integration

To address these gaps, I am developing a low-power wearable platform featuring the highest-grade Analog Front-Ends (AFE) currently available. My research explores a novel hardware-first solution to the "missing information" problem.

**Primary Research Question:**

* Can the integration of Deep-Infrared wavelengths (beyond 1000nm) provide additional physiological features in the PPG signal to improve the accuracy and generalizability of continuous BPM?

#### Work to Date & Roadmap

So far, I developed an experimental board to do sensor integration and explore different optical configurations (LED/Photodiode). I'm also implementing the firmware using Zephyr RTOS on an nRF52 platform to ensure low-power, real-time data acquisition. The next step would be data collection and signal analysis to identify the optimal optical path and wavelength combination.Finally, I will design a compact wearable version to generate large datasets including during everyday activity and test BPM models to answer my research question.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/exp_board.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/optics_board.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Experiment board for sensor integration and exploring different optical configurations.
</div>