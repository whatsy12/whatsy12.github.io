---
title: "Physarum slime mold behavior equation"
date: 2025-08-24 21:37:12
categories:
- Project
tags:
- Simulation
- Project
- English
---

# Base idea
<img width="400" height="650" alt="image" src="https://github.com/user-attachments/assets/4a138565-0efb-4983-adcb-cb298b463279" />

The basic simulation idea [2]

# 1. Sense
<img width="413" height="454" alt="image" src="https://github.com/user-attachments/assets/f4de8ed3-e317-43cc-8a82-a1aaa0a8cf4e" />

Used Algeomath to draw shapes [3]

The box represents the sensor.

$S_0$ = (sensor size)
\
$S_1$ = $2 \times$(sensor size)
\
$P_{x, y}$ = (Number of particles inside cell x, y)
\
$SP$ = (Number of particles inside sensor range)
\
\
$\alpha$ and $\beta$ could be calculated using the formula below.
\
($\alpha$, $\beta$) = ($x + \sin \theta \times DST$, $y + \cos \theta \times DST$)
\
\
SP could be calculated by the formula below.
\
$SP = \sum\limits_{i=-S_0}^{S_0} \sum\limits_{j=-S_0}^{S_0} P_{x + i, y + j}$
\
Equation from [1]
\
\
This opperation will be called $f(\theta)$ and will be used later

# 2. Rotate
<img width="691" height="512" alt="image" src="https://github.com/user-attachments/assets/a233e7a9-5f61-495c-8f0c-465f5733967e" />

Used Algeomath to draw shapes [3]

We will use the function we previously made in step 1.
\
In the image above, there are three boxes, which represents each unique sensor.
\
We will compare the unique sensor's $SP$ value, and we could decide the next rotation.
\
As you might see in the image, there are three boxes, or in other words three unique sensors.

The distance between $(\alpha, \beta)$ and $(x, y)$ is exactly $DST$.
\
Same for the other two alphas and betas.
\
\
$f(-\theta)$ is represented as $(\alpha, \beta)$
\
$f(0)$ is represented as $(\alpha', \beta')$
\
$f(\theta)$ is represented as $(\alpha'', \beta'')$
\
\
We will compare $f(-\theta)$, $f(0)$, $f(\theta)$ by the following method

<img width="332" height="303" alt="image" src="https://github.com/user-attachments/assets/41602c33-d225-47c8-bc7c-381890a02700" />

The rotating method [2]

# 3. Move
We could use the information from step 2 to move the agent.

$\Delta \theta =$ (Turn angle) $\times$ (Turn Speed) $\times \Delta$ Time
\
$\Delta x = \sin \theta \times$ (Speed)
\
$\Delta y = \cos \theta \times$ (Speed)
\
Calculation equation [1]

# 4. Diffuse & Decay
<img width="342" height="172" alt="image" src="https://github.com/user-attachments/assets/3e4ec0b9-f0bf-41a8-b2e5-3bb0db7fd7fd" />

Image from [2]

The slime while somewhat mix up with it's environment, and diffuse.
\
Also the slime will slowely evaporate.

Below is the mathamatical Diffuse, and decay model 

Sum = $\sum\limits_{i=-1}^{1} \sum\limits_{j=-1}^{1} P_{x + i, y + j}$ 
\
$P_{x, y} = P_{x, y} \times (1.0 -$ Diffuse Rate $) +$ Sum $\times$ Diffuse Rate - Decay rate $\times \Delta Time$

Calculation equation [1]


# References
1. https://github.com/SebLague/Slime-Simulation/blob/main/Assets/Scripts/Slime/SlimeSim.compute
2. https://cargocollective.com/sagejenson/physarum
3. https://www.algeomath.kr/algeo/main.do

# Algeomath images
https://github.com/whatsy12/projects/blob/main/PhysarumPolycephalumSimulation/Algeomath_snapshot_2025-8-24_17612_756.png
https://github.com/whatsy12/projects/blob/main/PhysarumPolycephalumSimulation/Algeomath_snapshot_2025-8-24_18628_860.png

Original post:

https://github.com/whatsy12/projects/blob/main/PhysarumPolycephalumSimulation/finalSimulation.md
