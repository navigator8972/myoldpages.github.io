---
title: "Robot learning with priors based on latent variables"
excerpt: ""
collection: portfolio
---


Improving data efficiency is one of the central challenges in robot learning because task examples and demonstrations are often expensive to acquire. One way to enable robots to learn from limited data is to employ domain priors. To effectively represent and incorporate these priors, this research explores approaches based on latent variables. The introduction of latent variables allows for a low-dimensional representation of task data and enforced structures, alleviating computational challenges in dealing with raw sensory data. Latent variables can also be used as a flexible intermediate representation to retain and transfer some useful structures to a target task. Lastly, with a prior design, latent variables might correlate the raw data to some intepretable values, or even abstract concepts to represent quite general model priors.

**Priors on Temporal Relation**

For one example, imagine the robot accesses a set of rolling ball data in the form of video streams. It is apparent that, despite of the high-dimensionality of raw data, the generation of rolling-ball pixels is governed by a low-dimensional (latent) process. The latent variables and their temporal relation can be simultaneously extracted through unsupervised learning with a variational treatment:

<p align="center">
<img src="/images/research/vaedyn.png" width=600>
 </p>

The learning routine ends with a posterior model which transforms raw data sequence to latent variables, a prior model which predicts the next latent variable if there is no observation, and a generation model which eventually allows to sample sequences similar to the learned data. Such an idea is not restricted to this rolling ball example. It is actually applicable to another example with an underlying dynamical process, e.g., the generation of dynamical handwriting images:

<p align="center">
<img src="https://raw.githubusercontent.com/navigator8972/vae_dyn/master/figs/0_0.gif" width="100"><img src="https://raw.githubusercontent.com/navigator8972/vae_dyn/master/figs/3_0.gif" width="100"><img src="https://raw.githubusercontent.com/navigator8972/vae_dyn/master/figs/6_0.gif" width="100"><img src="https://raw.githubusercontent.com/navigator8972/vae_dyn/master/figs/9_0.gif" width="100"><img src="https://raw.githubusercontent.com/navigator8972/vae_dyn/master/figs/0_1.gif" width="100"><img src="https://raw.githubusercontent.com/navigator8972/vae_dyn/master/figs/U_0.gif" width="100">
 </p>

Meanwhile, the extracted dynamics might be useful in addressing relevant tasks. For instance, the prior knowledge about the rolling ball movement could facilitate the learning of a ball-striking task, in which the robot needs to anticipate the ball trajectory and move a paddle to hit the ball towards a target. The latent variable representation makes the task learning much easier in a low-dimensional space:

<p align="center">
<img src="https://raw.githubusercontent.com/navigator8972/roboschool_baxterstriker/master/figs/sample_1.gif" width="150"><img src="https://raw.githubusercontent.com/navigator8972/roboschool_baxterstriker/master/figs/sample_2.gif" width="150"><img src="https://raw.githubusercontent.com/navigator8972/roboschool_baxterstriker/master/figs/sample_3.gif" width="150"><img src="https://raw.githubusercontent.com/navigator8972/roboschool_baxterstriker/master/figs/sample_4.gif" width="150">
 </p>
 
Note the robot does not need to always have the access to the visual input. In fact, the prior model allows robot to have an internal prediction about the future sensory input after the camera is switched off and still scores the goal with a model-based control.

**Priors on Data Modalities**

Another type of prior is explored to bridge task examples of different modalities. For instance, the robot is demonstrated with handwriting examples of two modalities: letter images and arm joint movements to form the letter trajectories. Both modalities of data can be of a high-dimensionality and each can be transformed to a latent representation as a compressed form. Moreover, the latent variable can be regarded as an abstract representation of the learning letter. This implies the latent variables from images and motion trajectories should be identical, because the two types of demonstrations are describing the same task abstraction through the lens of different sensor modalities.

The prior about this modal associativity can be enforced in the latent space of two deep generative models:

<p align="center">
<img src="/images/research/vaeassoc.png" width=500 align="center"/>
 </p>
 
 The latent space can thus be considered as overlapped manifolds that intepolate both letter images and motions:
 
 <p align="center">
<img src="/images/research/VAEAssoc_ViewerDemoTest.gif" width=600>
 </p>
 
 Exploiting such an associativity, one can obtain an end-to-end controller which infers handwriting motion from letter images:
 
 <img src="https://raw.githubusercontent.com/navigator8972/vae_assoc/master/fig/writing_test_camera.png" width=400> <img src="https://raw.githubusercontent.com/navigator8972/vae_assoc/master/fig/writing_incomplete_canvas.png" width=380>
 
 Note the full generative model of image modality can help when the input is not complete: one can first explore in the latent space to find the variable that complements the occluded part and then generate arm motion accordingly.
