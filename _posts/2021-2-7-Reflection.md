---
layout: post
title: 15-464 Technical Animation
---

### Lecture 2: Techniques for Creating Animation (cont.)
The cyclic coordinate descent IK algorithm was quite interesting. I'm guessing
the optimization procedure implicitly encodes the Jacobian(s), but it was
definitely intriguing to see how you could have an IK algorithm without ever
having to explicitly define the Jacobians, especially for applications where you
have very little information. Here's a cool paper on using cyclic coordinate
descent for protein loop closure: [paper link](https://pubmed.ncbi.nlm.nih.gov/12717019/).

The Cartoon Animation filter also made a good impression on me. I wonder if
we'll be able to have some general translation capabilities, e.g. from motion capture data
--> cartoon characters/different 3D models using a single filter such as the
Cartoon Motion Filter. Will update this post when I find out more.

### Lecture 1: Techniques for Creating Animation

Most of this lecture was familiar material for me, as I've previously taken
[60-125: Introduction to 3D Animation](http://cmuanimation.weebly.com/).
Nonetheless, it was nice to see the main types of 3D animation techniques
(Keyframe, Procedural, Physics-based, Motion Capture) formally presented, since
until now I've just learned about them through conversation.

Motion VAEs (MVAE), or _autoregressive conditional variational autoencoders_,
were new to me however. **Autoencoders** are neural networks that leverage
unsupervised learning in order to efficiently represent some set of input data.
In particular, they output a singular value for each state attribute.
**Variational autoencoders** are autoencoders that describe a probability
distribution, rather than a value, for each state attribute.

<center><img src="../images/model_VAE.png" style="height:350px"></center>
<center><span style="font-size:10px">Source: https://medium.com/deepgamingai/learning-sports-motions-with-autoregressive-variational-autoencoders-e89599d4cfd</span></center>

I wonder if they're similar to Model-Predictive Controllers? Will update this
post when I figure that out.
It's awesome to see that this class touches upon so many different fields. This
past weekend I've been brushing up on the basics of fluid dynamics, since my
final paper presentation is on [A Practical Octree Liquid Simulator With Adaptive
Surface Resolution](https://cs.uwaterloo.ca/~c2batty/papers/Ando2020/Ando2020.pdf).
Looking forward to an amazing semester!
