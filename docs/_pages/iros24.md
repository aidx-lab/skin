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
We distinguish two types of domain randomization: Inter-episode and intra-episode randomizations. The first type refers to parameters sampled at the beginning of an episode and then kept constant. The latter is sampled periodically throughout an episode.
While \\(N(\mu, \sigma)\\) denotes a normal distribution with mean $$\mu$$ and standard deviation $$\sigma$$, $$U(a, b)$$ and $$LogU(a, b)$$ denote a uniform and log-uniform distribution in the range from $$a$$ to $$b$$, respectively.

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
        <td align="center"> $$\text{N}\,\text{m}\,\text{rad}^{-1}$$ </td>
        <td align="center"> inter </td>
        <td align="center"> $$U(4.8, 5.2)$$ </td>
    </tr>
    <tr>
        <td align="left"> Damping gain </td> 
        <td align="center"> $$K_d$$ </td>
        <td align="center"> $$\text{N}\,\text{m}\,\text{s}\,\text{rad}^{-1}$$ </td>
        <td align="center"> inter </td>
        <td align="center"> $$U(0.26, 0.33)$$ </td>
    </tr>
    <tr>
        <td align="left"> Parasitic stiffness </td> 
        <td align="center"> $$K_e$$ </td>
        <td align="center"> $$\text{N}\,\text{m}\,\text{rad}^{-1}$$ </td>
        <td align="center"> inter </td>
        <td align="center"> $$U(15, 35)$$ </td>
    </tr>
    <tr>
        <td rowspan="2" align="left"> Stick friction </td> 
        <td align="center"> $$\mu_{\text{stick},1/2}$$ </td>
        <td align="center"> $$\text{N}\,\text{m}$$ </td>
        <td align="center"> inter </td>
        <td align="center"> $$U(0.01, 0.03)$$ </td>
    </tr>
    <tr>
        <td align="center"> $$\mu_{\text{stick},3}$$ </td>
        <td align="center"> $$\text{N}\,\text{m}$$ </td>
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
    <tr>
        <td rowspan="3" align="left"> Orientation offset </td> 
        <td align="center"> $$\psi$$ </td>
        <td align="center"> $$^\circ$$ </td>
        <td align="center"> inter </td>
        <td align="center"> n. a. </td>
        <td align="center"> $$U(-5, 5)$$ </td>
    </tr>
    <tr>
        <td align="center"> $$\theta$$ </td>
        <td align="center"> $$^\circ$$ </td>
        <td align="center"> inter </td>
        <td align="center"> n. a. </td>
        <td align="center"> $$U(-5, 5)$$ </td>
    </tr>
    <tr>
        <td align="center"> $$\phi$$ </td>
        <td align="center"> $$^\circ$$ </td>
        <td align="center"> inter </td>
        <td align="center"> n. a. </td>
        <td align="center"> $$0.0$$ </td>
    </tr>
    <tr>
        <td align="left"> Mass </td> 
        <td align="center"> $$m$$ </td>
        <td align="center"> $$\text{g}$$ </td>
        <td align="center"> inter </td>
        <td align="center"> $$U(3.0, 5.0)$$ </td>
        <td align="center"> $$U(5.0, 7.0)$$ </td>
    </tr>
    <tr>
        <td align="left"> Radius </td> 
        <td align="center"> $$R$$ </td>
        <td align="center"> $$\text{mm}$$ </td>
        <td align="center"> inter </td>
        <td align="center"> $$U(4.0, 8.0)$$ </td>
        <td align="center"> $$6.0$$ </td>
    </tr>
    <tr>
        <td align="left"> Lateral friction </td> 
        <td align="center"> $$\mu_\text{lat}$$ </td>
        <td align="center"> $$1$$ </td>
        <td align="center"> inter </td>
        <td align="center"> $$U(1.1, 1.3)$$ </td>
        <td align="center"> $$U(0.8, 1.0)$$ </td>
    </tr>
    <tr>
        <td align="left"> Spinning friction </td> 
        <td align="center"> $$\mu_\text{spin}$$ </td>
        <td align="center"> $$1$$ </td>
        <td align="center"> inter </td>
        <td colspan="2" align="center"> $$LogU(2\times10^{-3}, 2\times10^{-2})$$ </td>
    </tr>
    <tr>
        <td align="left"> Random forces </td> 
        <td align="center"> $$F_\text{rand}$$ </td>
        <td align="center"> $$N$$ </td>
        <td align="center"> intra </td>
        <td colspan="2" align="center"> $$U(-4\times10^{-3}, 4\times10^{-3})$$ </td>
    </tr>
</table>​

### Skin Parameters

<table>
    <tr>
        <th colspan="2" align="left"> Parameter </th>
        <th align="center"> Unit </th>
        <th align="center"> Type </th>
        <th align="center"> Distribution </th>
    </tr>
    <tr>
        <td rowspan="3" align="left"> Sensor position </td> 
        <td align="center"> $$y$$ </td>
        <td align="center"> $$\text{mm}$$ </td>
        <td align="center"> inter </td>
        <td align="center"> $$U(21.5, 25.5)$$ </td>
    </tr>
    <tr>
        <td align="center"> $$\beta$$ </td>
        <td align="center"> $$^\circ$$ </td>
        <td align="center"> inter </td>
        <td align="center"> $$U(-12, 12)$$ </td>
    </tr>
    <tr>
        <td align="center"> $$\alpha$$ </td>
        <td align="center"> $$^\circ$$ </td>
        <td align="center"> inter </td>
        <td align="center"> $$U(-15, 15)$$ </td>
    </tr>
    <tr>
        <td align="left"> Elasticity </td> 
        <td align="center"> $$E$$ </td>
        <td align="center"> $$\text{MPa}\,\text{m}^{-1}$$ </td>
        <td align="center"> inter </td>
        <td align="center"> $$U(236, 848)$$ </td>
    </tr>
    <tr>
        <td align="left"> Scale </td> 
        <td align="center"> $$S_j$$ </td>
        <td align="center"> $$\text{N}^{-1}$$ </td>
        <td align="center"> inter </td>
        <td align="center"> $$U(61, 76)$$ </td>
    </tr>
    <tr>
        <td align="left"> Taxel offsets </td> 
        <td align="center"> $$T_\text{off}$$ </td>
        <td align="center"> $$1$$ </td>
        <td align="center"> inter </td>
        <td align="center"> $$U(-5, 5)$$ </td>
    </tr>
    <tr>
        <td align="left"> Noise range </td> 
        <td align="center"> $$\sigma_\text{taxel}$$ </td>
        <td align="center"> $$1$$ </td>
        <td align="center"> inter </td>
        <td align="center"> $$U(0, 5)$$ </td>
    </tr>
    <tr>
        <td align="left"> Taxel noise </td> 
        <td align="center"> $$T_\text{noise}$$ </td>
        <td align="center"> $$1$$ </td>
        <td align="center"> intra </td>
        <td align="center"> $$N(0, \sigma_\text{noise})$$ </td>
    </tr>
</table>​

---

## Learning Configuration

### Reward Constants

<table>
    <tr>
        <th></th>
        <th align="center"> $$\lambda_p$$</th>
        <th align="center"> $$\lambda_g$$</th>
        <th align="center"> $$\lambda_f$$</th>
        <th align="center"> $$\lambda_\alpha$$</th>
        <th align="center"> $$\lambda_q$$</th>
        <th align="center"> $$\lambda_\dot{q}$$</th>
        <th align="center"> $$\lambda_\tau$$</th>
    </tr>
    <tr>
        <th align="Left"> Marble </th>
        <td align="center"> $$0.15$$ </td> 
        <td align="center"> $$0.05$$ </td> 
        <td align="center"> $$0.05$$ </td> 
        <td align="center"> n. a. </td> 
        <td align="center"> $$0.01$$ </td> 
        <td align="center"> $$0.01$$ </td> 
        <td align="center"> $$0.01$$ </td> 
    </tr>
    <tr>
        <th align="Left"> Bolt </th>
        <td align="center"> $$0.15$$ </td> 
        <td align="center"> $$0.05$$ </td> 
        <td align="center"> $$0.05$$ </td> 
        <td align="center"> $$0.05$$ </td> 
        <td align="center"> $$0.01$$ </td> 
        <td align="center"> $$0.01$$ </td> 
        <td align="center"> $$0.01$$ </td> 
    </tr>
</table>

### Learning Parameters

<table>
    <tr>
        <th> Parameter </th>
        <th> Value </th>
    </tr>
    <tr>
        <td> Number of environments </td>
        <td> $$8$$ </td>
    </tr>
    <tr>
        <td> Replay buffer sixe </td>
        <td> $$2 \times 10^5$$ </td>
    </tr>
    <tr>
        <td> Steps before learning </td>
        <td> $$6000$$ </td>
    </tr>
    <tr>
        <td> Training interval </td>
        <td> $$60\,\text{steps}$$ </td>
    </tr>
    <tr>
        <td> Gradient steps </td>
        <td> $$200$$ </td>
    </tr>
    <tr>
        <td> Discount factor </td>
        <td> $$0.95$$ </td>
    </tr>
    <tr>
        <td> Polyak update </td>
        <td> $$5\times 10^{-3}$$ </td>
    </tr>
    <tr>
        <td> Target entropy </td>
        <td> $$-4.0$$ </td>
    </tr>
    <tr>
        <td> Initial entropy coefficient </td>
        <td> $$0.2$$ </td>
    </tr>
    <tr>
        <td> Learning rate </td>
        <td> $$3\times 10^{-4}$$ </td>
    </tr>
    <tr>
        <td> Batch size </td>
        <td> $$256$$ </td>
    </tr>
</table>