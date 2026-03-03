---
permalink: /icra26
layout: page
title: ICRA 26
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

    @inproceedings{kasolowsky2024,
        author = {Ulf Kasolowsky and Berthold B{\"a}uml},
        title = {Learning Controlled Separation of Small Objects Between Two Fingers with a Tactile Skin},
        year = {2024}
    }
 
---

## Domain Randomization
We distinguish two types of domain randomization: Inter-episode and intra-episode randomizations. The first type refers to parameters sampled at the beginning of an episode and then kept constant. The latter is sampled periodically throughout an episode.
While $$N(\mu, \sigma)$$ denotes a normal distribution with mean $$\mu$$ and standard deviation $$\sigma$$, $$U(a, b)$$ and $$LogU(a, b)$$ denote a uniform and log-uniform distribution in the range from $$a$$ to $$b$$, respectively.