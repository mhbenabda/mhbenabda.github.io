---
layout: page
title: Deep Learning Reconstruction of Optoacoustic images on FPGA
description: Deep Learning on AMD Kria™ K26 SOM optimized for the DPU
img: assets/img/p4_thumbnail.jpg
importance: 4
category: work
---

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/p4_thumbnail.jpg" title="p4_thumbnail" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Autoencoder running on KRIA K26 for reconstruction of ultrasound imaging signal.
</div>

## Overview
The standard reconstruction of optoacoustic images (similar to ultrasound) is **Delay and Sum** which is an inverse problem that quickly requires a high computational load for a high resolution image. Advanced imaging in the last 20 years became possible due to the availability of computational power, however Delay & Sum is very innefficient on GPUs. This is due to the non-trivial indexing and irregular memory access caused by the data dependancy involved in this methode; each pixel involves signals from many sensors. 
My goal is to develop a real-time image reconstruction using deep learing which would be optimized for today's AI hardware. 

<div class="row justify-content-center">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/p4_delay.jpg" title="p4_delay" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
</div>

## Optoacoustic
Optoacoustic is 

<div class="row justify-content-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/p4_opto.png" title="p4_opto" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
</div>