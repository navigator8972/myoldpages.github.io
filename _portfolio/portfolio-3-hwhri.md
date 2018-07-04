---
title: "Human-robot interaction for children handwriting acquisition - CoWriter"
excerpt: ""
collection: portfolio
---

This research contributes to the [**CoWriter**](https://gaips.inesc-id.pt/component/gaips/projects/showProject/10/27) project, which aims to build a robotic system that interacts with children to help them to acquire handwriting skills. The research exploits the idea of *learning-by-teaching* framework: the robot plays the role of a learner while children polish their skills in teaching the robot. 

<p align="center">
<img src="{{site.baseurl}}/images/research/naoandchild.JPG" width="200" alt=""><img src="{{site.baseurl}}/images/research/naowriting.png" width="270" alt=""><img src="{{site.baseurl}}/images/research/childwriting.JPG" width="200" alt="">
</p>

Machine learning techniques are used to learn from adult handwriting examples and generate similar/poorly-written samples by perturbing the model parameters. However, it is inadequate to learn with a direct feature representation, such as the coordinates of 2D points. Natural handwriting movement has many informative features in terms of motion smoothness, stroke segmentation and path geometries. A perturbation in such a feature space can be much more effective and intuitive to generate desired handwriting variations. Bearing this in mind, we learn the generative process with a kind of lognormal human kinematics model (see O'Reilly and Plamondon, Pattern Recognition, 2009). The parameters of lognormal model correlate to some useful kinematic and geometric features of handwriting motion, such as stroke velocity and angular positions. The learned model is a probabilistic distribution over these feature parameters, which manages to generate human-like dynamical handwriting motion if we take samples from the parameter configurations with a high probability mass.

<p align="center">
<img src="https://raw.githubusercontent.com/navigator8972/pytrajkin/master/fig/A_synthetic_sample_animated.gif" width="90"><img src="https://raw.githubusercontent.com/navigator8972/pytrajkin/master/fig/B_synthetic_sample_animated.gif" width="90"><img src="https://raw.githubusercontent.com/navigator8972/pytrajkin/master/fig/Dc_synthetic_sample_animated.gif" width="90"><img src="https://raw.githubusercontent.com/navigator8972/pytrajkin/master/fig/d_synthetic_sample_animated.gif" width="90">
<img src="https://raw.githubusercontent.com/navigator8972/pytrajkin/master/fig/e_synthetic_sample_animated.gif" width="90"><img src="https://raw.githubusercontent.com/navigator8972/pytrajkin/master/fig/Q_synthetic_sample_animated.gif" width="90"><img src="https://raw.githubusercontent.com/navigator8972/pytrajkin/master/fig/w_synthetic_sample_animated.gif" width="90"><img src="https://raw.githubusercontent.com/navigator8972/pytrajkin/master/fig/y_synthetic_sample_animated.gif" width="90">
  </p>

On the other hand, we can also generate unnatural letter profiles with unlikely parameter configurations. In fact, the deformations can be controlled as there is a clear connection between the stroke geometry and magnitude of feature parameters (see the left figure below). We use these models in an HRI system, where the robot demonstrates three typical children handwriting errors in the beginning and gradually improves during the learning session. Human studies show that children are aware of the learning capability of robots and can benefit from interacting with such a robotic companion.

<p align="center">
<img src="{{site.baseurl}}/images/research/PyTrajKin_DemoComp.gif" width="300" alt="">    <img src="{{site.baseurl}}/images/research/naowriting_architecture.png" width="270" alt="">
</p>

Find more in:

Papers:

[Do Children Perceive Whether a Robotic Peer is Learning or Not]({{site.baseurl}}/publication/2018-01-01-hri2018)

[Affect of Robot’s Competencies on Children’s Perception]({{site.baseurl}}/publication/2017-12-01-aamas2017)

[Synthesizing Robotic Handwriting Motion by Learning from Human Demonstrations]({{site.baseurl}}/publication/2016-07-01-ijcai2016)

Repositories:

[nao_writing](https://github.com/navigator8972/nao_writing)

[pytrajkin](https://github.com/navigator8972/pytrajkin)

