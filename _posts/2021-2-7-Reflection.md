---
layout: post
title: 15-464 Technical Animation
---

### Lecture 3: Inverse Kinematics
Talking a little bit more on the Cyclic Coordinate Descent IK algorithm and just
generally talking about Jacobians was nice. I was already familiar with Jacobian
transpose IK from 15-462: Computer Graphics, and in fact did not know that there
were other ways of doing IK, so these past 2 classes have been somewhat
eye-opening.

Reading the [CCD paper](http://www.virtualpuppetry.com/inverse_kinematics_ccd/paper.pdf) and also having it presented to me during class, I realize
that I haven't really been considering the
visual/artistic consequences of CG algorithms. This is sort of a trivial
insight, but manipulating the order in which you update the joint chain in
order to produce certain effects that shape a 3D character was kind of amazing
to me; I imagine that 3D animation studios probably tend towards updating the
ends of the joint chains more so than the base joints, since you can encode so
much emotion and character in the hands and the fingers.

<center><img src="../images/pixar_lamp.jpg" style="height:350px"></center>
<center><span style="font-size:10px">Source: https://www.artstation.com/artwork/LXRz0
</span></center>

I had also never considered using a recursive optimization scheme (i.e.
"Bouncing") in IK, though upon reflection it seems like a fairly straightforward
idea. An interesting thing to note is that Levenberg-Marquadt (Damped Least-Squares)
is used in both IK robotics applications as well SLAM robotics problems. In a
way, I'm guessing you can model time series data in SLAM applications just like
a really long/complex joint hierarchy; each joint is a keyframe observation, and
since the robot is using the information at each "joint" to localize itself and
update the map, these keyframes are connected as a chain.  Not sure if this insight is particularly innovative, but that was a fairly good highlight of the day for me. Nonlinear optimization techniques are truly universal.

I might try to add some new IK techniques, such as CCD, any of the modified CCD
techniques, Inverse Jacobian methods, etc. to the 15-462 Computer Graphics
codebase (if le Max Slater doesn't implement everything first lol).


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
