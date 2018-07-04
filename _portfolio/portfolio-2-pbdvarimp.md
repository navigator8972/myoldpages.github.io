---
title: "Learning impedance controllers from demonstrations"
excerpt: ""
collection: portfolio
---

Robots need to regulate contact force in order to gracefully interact with the physical world. Impedance control is an implicit approach to achieve this. In impedance control, the robot does not directly measure and control the contact force but focuses on modulating its own dynamic behavior under the external wrench. For instance, a robot can act like a low-stiffness spring, which makes the regulation point, e.g., robot end-effector, yield to the external wrench so as to avoid a large contact force.

This research is about how can we let robots learn such kind of impedance controllers from demonstrations. This of course requires some assumptions about the robot dynamic behavior. One way is to assume that the robot adopts a constant impedance (taking stiffness as an example) parameter within a specific time window and tends to track a desired position and force profile. With additional constraints, one can formulate an optimization problem to extract a stiffness trajectory characterizing how the robot should react in face of motion deviation. We realize such an approach on a multi-fingered hand to realize compliant rotational motion. Now the dynamic behavior to describ is not the end-effector of a single manipulator but the manipulated object. The idea is to model and control the object behavior through a *virtual-frame* representation, which uses finger joint configurations and tactile sensing to surrogate the real object pose. 

<p align="center">
<img src="{{site.baseurl}}/images/research/allegro_biotac.png" width="270" alt=""><img src="{{site.baseurl}}/images/research/virtual_frame.png" width="270" alt="">
</p>

With recorded tactile information and object (a bulb) motion as demonstrations, the robot learns to insert the bulb into a socket with a variable impedance profile, e.g., increasing the motion stiffness at the end stage to overcome more frictions.

<p align="center">
<img src="{{site.baseurl}}/images/research/allegro_bulb_demo.gif" width="270" alt=""><img src="{{site.baseurl}}/images/research/allegro_bulb_exec.gif" width="270" alt="">
</p>

