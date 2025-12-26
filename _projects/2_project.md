---
layout: page
title: CoughNet
description: Ultra-Low Power Embedded AI for Respiratory Monitoring
img: assets/img/cough_square.png
importance: 2
category: work
giscus_comments: true
---

## Overview
CoughNet is an end-to-end Machine Learning project I did in the context of a project based course I took at ETH called "Machine Learning on Microcontrollers". I wanted to achieve continuous, 24/7 monitoring of cough frequency to assess the severity of respiratory diseases and the efficacy of antitussive therapies. By deploying high-performance inference directly on a micrcontroller, I wanted to adress critical requirement for patient privacy and create a proof-of-concept for ultra-low power healthcare monitoring in a wearable form factor. 

## Hardware-Software Codesing
The core innovation of CoughNet lies in its hardware-optimized architecture. While traditional audio classification relies on MFCC (Mel-frequency cepstral coefficients) for feature extraction, this process can consume over 2x more power than the actual neural network inference.

To solve this I used the MAX78000 AI microcontroller which has a CNN accelerator as a target device, and I designed an optimized 1D-CNN architechture that processees raw audio windows directly. 

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/p2_arch.jpg" title="p2_arch" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Target Device Architecture
</div>

##### Key Features:
- Dual core: Arm Cortex-M4 + RISC-V Coprocessor​
- **Convolutional Neural Network Accelerator**​
- 512KB Flash​
- 128KB SRAM

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/p2_optimized.jpg" title="p2_optimized" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Method Comparision.
</div>

## Dataset and Preprocessing
The model was trained on the COUGHVID crowdsourcing dataset from the EPFL Embedded Systems Laboratory, featuring approximately 30,000 samples. A pre-existing model was used to filter the dataset from bad samples usually present in crowd-sourced data. Then, I applied **downsampling** to 16kHz to reduce memory without reducing cough information in the signal, **segmentation** to keep only the parts of the signal were there is a cough sound using standard signal processing, **cropping** into 1s overlapping windows, and finally **augmentation** by stretching, shifting and adding different background noises.

Additionally, some standard keyword classes were added to make the model a bit more complex than just a binary classification. 

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/p2_preprocessing.jpg" title="p2_preprocessing" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Preprocessing Pipeline
</div>

## Neural Network Architecture
In my work I explored the trade-off between using a pure 1D-CNN (CoughNet1) and a hybrid 1D and 2D-CNN (CoughNet2) architecture. Both were trained using **Quantization Aware Training** on 20 classes (Cough class + 18 Keywords + Unknown) for 100 epochs. 
The best model depends on the application constraints and priorities. While after tuning the models, I was was able to reach similar accuracy for both, the difference was in the inference latency, size, and energy consumption per inference. The pure 1D-CNN was faster, used less operations per inference which makes it lower power, but was bigger in size.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/p2_1d.jpg" title="p2_1d" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="caption">
    Pure 1D-CNN Model
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/p2_2d.jpg" title="p2_2d" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="caption">
    Hybrid 1D + 2D-CNN Model
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/p2_comp.jpg" title="p2_comp" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Performance comparision of pure 1D-CNN and hybrid 1D+2D-CNN model
</div>

## Model Evaluation & Results
