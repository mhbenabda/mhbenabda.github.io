---
layout: page
title: Non-invasive Tactile Stimulation
description: Controller for tTENS to non-invasively provide tactile sensory feedback for non-disabled subjects
img: assets/img/p3_thumbnail.jpg
importance: 3
category: work
---

## Definition
**TENS:** A transcutaneous electrical nerve stimulation is a device that produces mild electric current to stimulate the nerves. Targeted TENS (tTENS) is when specific nerves are targeted.

## Overview
It's very interesting for amputies as well as for VR applications to provide artificial tactile feedback to the user by generating a stimulation as close as possible to the natural encoding of touch. The encoding could be generated using standard or neuromorphic AI. Then it needs to be transformed into a physical stimulation to the user. For obvious reasons, the non-invasive ways is very tempting and could open many doors for interesting products.

Here I develop a hardware/software platform to flexibly generate TENS patterns and design psychophysics experiments using a Digitimer DS8R TENS unit and D188 Electrode selector. The goal is to leverage the bi-phasic stimulation and multi-channel capabilities of these two devices to further investigate the use of tTENS as a viable method for sensory feedback. The broader goal is to evaluate how tTENS can be combined with neuromorphic technologies to emulate natural tactile sensations more effectively.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/p3_overview.png" title="p3_overview" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Stimulation Setup. Highlighted are the hand region felt when the wrist nerves are stimulated.
</div>

## Functionning Principle
The stimulation process happens in three steps:
- **Mapping:** Mapping consist in finding the areas in the wrist, elbow or amputee's residual limb that provoke a distal percept in the (phantom) hand. This is possible by stimulating the peripheral nerves, mainly the median and ulnar nerves. The location of the electrode will influence the strength and quality of the referred sensation
- **Calibration:** The calibration step consists in tuning the stimulation parameters for each stimulation location to understand and improve the evoked sensation. The most commonly performed experiment is to generate a psychofunction for detecting the minimum threshold. 

The stimulation parameter space is large (Amplitude, frequency, pulse duration, recovery phase ratio, and interphase duration) and needs to be explored strategicaly. For that, I chose to use the adaptive psychophysical method such as the "Staircase method" and "Maximum-likelihood and Bayesian method" for their efficiency and focus around the region of interest, typically near the threshold. 

<div class="row justify-content-center">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/p3_calib.png" title="p3_calib" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Minimum Stimulation Threshold Detection. (Channel 3 overshoots due to error in electrode placement)
</div>

- **Stimulation:** Once the psychofunction is defined, it is used as a mapping function from the tactile sensor input in case of a prosthetic arm or from the virtual world input in case of VR, that will be after processing transformed into an electrical stimulation.

## Platform
The advantage of the Digitimer DS8R Stimulator is that it can generate charge-balanced biphasic rectangular pulses as the fundamental building blocks. This could reduce discomfort which is a common issue associated with noninvasive monophasic stimulation or excessive charge density.
Additionally, Current-controlled stimulation ensures safety by regulating the charge density delivered by each waveform regardless of the impedance at the electrode-skin interface.

<div class="row justify-content-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/p3_platform.png" title="p3_platform" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Hardware Setup
</div>

## Software
The software can be divided into 4 parts:
- API library with custom functions to controll the Digitimer instruments.
- Arduino code to transform the computer commands into specific trigger sequences, as well as to use the analog amplitude control on the device for a faster response time.
- GUI using Qt for the experiment window to interract with the user during the psychophysics experiment.
- Configurable experiment scripts that will run in the backend.

## Links
[Repo](https://github.com/mhbenabda/tTENS)
[Digitimer DS8R](https://www.digitimer.com/product/human-neurophysiology/peripheral-stimulators/ds8r-biphasic-constant-current-stimulator/)
[Digitimer D188](https://www.digitimer.com/product/human-neurophysiology/stimulator-accessories/d188-remote-electrode-selector/d188-remote-electrode-selector/)