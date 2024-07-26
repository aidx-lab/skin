---
permalink: /iros24
layout: page
title: IROS24
usemathjax: true
---
## Fine Manipulation Using a Tactile Skin: Learning in Simulation and Sim-to-Real Transfer

This site complements our paper [**Fine Manipulation Using a Tactile Skin: Learning in Simulation and Sim-to-Real Transfer**](){:target="_blank"} by
[Ulf Kasolowsky](https://www.linkedin.com/in/kasolowsky/){:target="_blank"} and [Berthold Bäuml](https://scholar.google.com/citations?hl=en&user=fjvpDsEAAAAJ){:target="_blank"} submitted to the 2024 IEEE/RSJ International Conference on Intelligent Robots and Systems.

<p align="center">
<img src="/skin/assets/imgs/iros24/front.png" alt="drawing" width="800"/>
</p>

## Abstract

We want to enable fine manipulation with a multi-fingered robotic hand by using modern deep reinforcement learning methods. 
Key for fine manipulation is a spatially resolved tactile sensor.
Here, we present a novel model of a tactile skin that can be used together with rigid-body (hence fast) physics simulators. 
The model considers the softness of the real fingertips such that a contact can spread across multiple taxels of the sensor depending on the contact geometry. 
We calibrate the model parameters to allow for an accurate simulation of the real-world sensor. 
For this, we present a self-contained calibration method without external tools or sensors.
To demonstrate the validity of our approach, we learn two challenging fine manipulation tasks: Rolling a marble and a bolt between two fingers. 
We show in simulation experiments that tactile feedback is crucial for precise manipulation and reaching sub-taxel resolution of < 1 mm despite a taxel spacing of 4 mm. 
Moreover, we demonstrate that all policies successfully transfer from the simulation to the real robotic hand.