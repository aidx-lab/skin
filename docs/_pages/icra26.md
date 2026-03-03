---
permalink: /icra26
layout: page
title: ICRA 2026
usemathjax: true
---
## Learning Controlled Separation of Small Objects Between Two Fingers with a Tactile Skin

This site complements our paper [**Learning Controlled Separation of Small Objects Between Two Fingers with a Tactile Skin**](){:target="_blank"} by
[Ulf Kasolowsky](https://www.linkedin.com/in/kasolowsky/){:target="_blank"} and [Berthold Bäuml](https://scholar.google.com/citations?hl=en&user=fjvpDsEAAAAJ){:target="_blank"} accepted for the 2026 IEEE International Conference on Robotics and Automation.

<p align="center" style="margin: 0">
<iframe class="youtube-video" width="746" height="420" src="https://www.youtube.com/embed/JhGAiLqrXUA?si=_xKkztDWUP5QZhUG" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</p>

## Abstract

We introduce and solve the novel task of controlled separation of small objects with two fingers of a multi-purpose robotic hand: after grasping into a box of small objects, the task is to drop as many of them until a desired number larger or equal to 1 remains between the fingers. Here, "small" means relative to the width of the fingers (or grippers) but also in absolute terms, in our case handling little pellets with a diameter of only 6mm.
We show that the task can be performed purely tactile using a spatially-resolved tactile skin on a fingertip. The separation policy is trained in simulation using reinforcement learning with a simple natural reward. In simulation experiments, we provide an exhaustive analysis of the benefits of using spatially-resolved tactile feedback: while an ideal (high-resolution) tactile sensor allows solving the task almost perfectly, a sensor with lower spatial resolution (here 4x4 taxels) still leads to an improvement of up to 20% compared to using only the fingers' joint sensors. For this analysis, we further train an estimator alongside the policy that predicts the ground truth contact positions. Finally, we demonstrate the successful sim-to-real transfer for the DLR-Hand II equipped with a tactile skin.

![Sequence](/skin/assets/imgs/icra26/front.png)

Cite this paper as:

    @inproceedings{kasolowsky2026,
        author = {Ulf Kasolowsky and Berthold B{\"a}uml},
        title = {Learning Controlled Separation of Small Objects Between Two Fingers with a Tactile Skin},
        year = {2024}
    }
 
---

## Domain Randomization
We distinguish two types of domain randomization: Inter-episode and intra-episode randomizations. The first type refers to parameters sampled at the beginning of an episode and then kept constant. The latter is sampled periodically throughout an episode.
While $$N(\mu, \sigma)$$ denotes a normal distribution with mean $$\mu$$ and standard deviation $$\sigma$$, $$U(a, b)$$ and $$LogU(a, b)$$ denote a uniform and log-uniform distribution in the range from $$a$$ to $$b$$, respectively.


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
        <td align="center"> $$U(0.03, 0.05)$$ </td>
    </tr>
    <tr>
        <td align="left"> Lateral friction </td> 
        <td align="center"> $$\mu_\text{lat}$$ </td>
        <td align="center"> $$1$$ </td>
        <td align="center"> inter </td>
        <td align="center"> $$U(0.8, 1.5)$$ </td>
    </tr>
    <tr>
        <td align="left"> Spinning friction </td> 
        <td align="center"> $$\mu_\text{spin}$$ </td>
        <td align="center"> $$1$$ </td>
        <td align="center"> inter </td>
        <td colspan="2" align="center"> $$U(0.0, 0.2)$$ </td>
    </tr>
</table>​