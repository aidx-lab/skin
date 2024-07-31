---
permalink: /iros24
layout: page
title: IROS24
usemathjax: true
---
## Fine Manipulation Using a Tactile Skin: Learning in Simulation and Sim-to-Real Transfer

This site complements our paper [**Fine Manipulation Using a Tactile Skin: Learning in Simulation and Sim-to-Real Transfer**](){:target="_blank"} by
[Ulf Kasolowsky](https://www.linkedin.com/in/kasolowsky/){:target="_blank"} and [Berthold Bäuml](https://scholar.google.com/citations?hl=en&user=fjvpDsEAAAAJ){:target="_blank"} presented at the 2024 IEEE/RSJ International Conference on Intelligent Robots and Systems.

## Abstract

We want to enable fine manipulation with a multi-fingered robotic hand by using modern deep reinforcement learning methods. 
Key for fine manipulation is a spatially resolved tactile sensor.
Here, we present a novel model of a tactile skin that can be used together with rigid-body (hence fast) physics simulators. 
The model considers the softness of the real fingertips such that a contact can spread across multiple taxels of the sensor depending on the contact geometry. 
We calibrate the model parameters to allow for an accurate simulation of the real-world sensor. 
For this, we present a self-contained calibration method without external tools or sensors.
To demonstrate the validity of our approach, we learn two challenging fine manipulation tasks: Rolling a marble and a bolt between two fingers. 
We show in simulation experiments that tactile feedback is crucial for precise manipulation and reaching sub-taxel resolution of < 1 mm (despite a taxel spacing of 4 mm). 
Moreover, we demonstrate that all policies successfully transfer from the simulation to the real robotic hand.
<p align="center">
<img src="/skin/assets/imgs/iros24/front.png" alt="drawing" width="800"/>
</p>

Cite this paper as:

    @inproceedings{Kasolowsky.2024,
        author = {Ulf Kasolowsky and Berthold B{\"a}uml},
        booktitle = {IEEE International Conference on Intelligent Robots and Systems},
        title = {Fine Manipulation Using a Tactile Skin: Learning in Simulation and Sim-to-Real Transfer},
        year = {2024}
    }
    
---

## Domain Randomization

### Finger Parameters

<table>
    <tr>
        <th colspan="2" align="left"> Parameter </th>
        <th align="center"> Unit </th>
        <th align="center"> Type </th>
        <th align="center"> Distribution </th>
    </tr>
    <tr>
        <td align="left"> Joint offsets </td> 
        <td align="center"> $$q_\text{off}$$ </td>
        <td align="center"> $$\text{rad}$$ </td>
        <td align="center"> inter </td>
        <td align="center"> $$U(-0.04, 0.04)$$ </td>
    </tr>
    <tr>
        <td align="left"> Joint noise </td> 
        <td align="center"> $$q_\text{noise}$$ </td>
        <td align="center"> $$\text{rad}$$ </td>
        <td align="center"> intra </td>
        <td align="center"> $$N(0.0, 0.02)$$ </td>
    </tr>
    <tr>
        <td align="left"> Proportional gain </td> 
        <td align="center"> $$K_p$$ </td>
        <td align="center"> $${\text{N}\,m\,rad}^{-1}$$ </td>
        <td align="center"> inter </td>
        <td align="center"> $$U(4.8, 5.2)$$ </td>
    </tr>
    <tr>
        <td align="left"> Damping gain </td> 
        <td align="center"> $$K_d$$ </td>
        <td align="center"> $$\text{N\,m\,s\,rad}^{-1}$$ </td>
        <td align="center"> inter </td>
        <td align="center"> $$U(0.26, 0.33)$$ </td>
    </tr>
    <tr>
        <td align="left"> Parasitic stiffness </td> 
        <td align="center"> $$K_e$$ </td>
        <td align="center"> $$\text{N\,m\,rad}^{-1}$$ </td>
        <td align="center"> inter </td>
        <td align="center"> $$U(15, 35)$$ </td>
    </tr>
    <tr>
        <td rowspan="2" align="left"> Stick friction </td> 
        <td align="center"> $$\mu_{\text{stick},1/2}$$ </td>
        <td align="center"> $$\text{N\,m}$$ </td>
        <td align="center"> inter </td>
        <td align="center"> $$U(0.01, 0.03)$$ </td>
    </tr>
    <tr>
        <td align="center"> $$\mu_{\text{stick},3}$$ </td>
        <td align="center"> $$\text{N\,m}$$ </td>
        <td align="center"> inter </td>
        <td align="center"> $$U(0.07, 0.09)$$ </td>
    </tr>
</table>​

### Object Parameters

<table>
    <tr>
        <th rowspan="2" colspan="2" align="left"> Parameter </th>
        <th rowspan="2" align="center"> Unit </th>
        <th rowspan="2" align="center"> Type </th>
        <th colspan="2" align="center"> Distribution </th>
    </tr>
    <tr>
        <th align="center"> Marble </th>
        <th align="center"> Bolt </th>
    </tr>
    <tr>
        <td align="left"> Position offset </td> 
        <td align="center"> $$\Delta x$$ </td>
        <td align="center"> $$\text{mm}$$ </td>
        <td align="center"> inter </td>
        <td colspan="2" align="center"> $$U(-2.0, 2.0)$$ </td>
    </tr>
</table>​

### Skin Parameters


---

## Learning Configuration

### Reward Constants

### Learning Parameters