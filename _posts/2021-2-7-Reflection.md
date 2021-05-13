---
layout: post
title: 15-464 Technical Animation
---

### Lecture 26: Learning
TODO

### Lecture 25: More Character Simulation
We went over this paper today:
http://calab.hanyang.ac.kr/papers/flexLoco.html

### Lecture 24: Character Simulation
TODO

### Lecture 23: Human Body
TODO

### Lecture 22: Faces
TODO

### Lecture 21: Paper Session IV
TODO

### Lecture 20: Deformables
TODO

### Lecture 19: Paper Session III
I presented the paper: A Practical Octree Liquid Simulator With Adaptive Surface Resolution
by Ryoichi Ando and Christopher Batty.

[Presentation:] (https://docs.google.com/presentation/d/1zY2X1k7xijIj54G-MsUvgtDtAX3RoaoV-HaeBR79uUA/edit?usp=sharing)

### Lecture 18: More Fluids
TODO

### Lecture 17: Fluids
TODO
#### Eulerian Finite Difference Based Approach to Solving Navier-Stokes

#### Stable Fluids

### Lecture 16: Mini-Project 2
I implemented most of UC Berkeley's CS248 Cloth Simulation Assignment, save for
self-collisions.

[Presentation](https://docs.google.com/presentation/d/1-tU_UICYNA3KLXLsrOzVfn5IgqjLY78sUKG-NWB8ETU/edit?usp=sharing)

### Lecture 15: More Final Project Pitches + Extra Content
TODO

### Lecture 14: Final Project Pitches
I am working with Max Slater for the final project on Position-Based Fluids:

[Project Proposal](https://docs.google.com/presentation/d/1-tU_UICYNA3KLXLsrOzVfn5IgqjLY78sUKG-NWB8ETU/edit?usp=sharing)

### Lecture 13: Paper Session II
TODO

### Lecture 12: Final Projects & Rigid Bodies
Final projects look cool, looking forward to seeing what everyone does!

I didn't consider that parallelization could be leveraged for much better
results. I'm wondering if we could adopt a Russian-Roulette scheme for spatial
locality to avoid bias in the partitioning?

More impulse-based collision handling.

### Lecture 11: More Cloth
Gotta say that the impulse collision handling paper is also a very likable paper
for me ;) this is such a great idea! In general I'm beginning to learn that
there is quite a significant difference between "physically-based" and "physically-motivated". I'm wondering how this framework would work with rips in the cloth, since here the collisions are super important and should not be avoided. I could also definitely see this in production for some 3D animation film, since this scheme seems to work pretty reliably.

For the "Estimating Cloth Simulation Parameters from Video" paper,
the "knit" result was less compelling than the others due to the absence of the
actual texture of the cloth, but otherwise the results were awesome!

The use of structured light to eliminate lighting/BRDF effects was very nice. In
general this was a well-thought out paper and I'm quite impressed. A lot of the
other papers in this class use some form of deep learning to further optimize
results, I'm wondering if that's a possible extension here with formulating an
even better loss function?

### Lecture 10: Simulation and Cloth
Went over forward/implicit/symplectic Euler, Verlet, Runge-Katta (RK4)
integration techniques. RK4 is also used in robotics!

The Large Steps in Cloth Simulation paper was pretty cool, it's awesome that
the authors can claim that numerical stability is not an issue for them, it
seems like large time steps with reasonable constraints is the way to go.

The unified particle physics paper is pretty relevant to the position based
fluid simiulation I'm doing with Max (Matthias Muller is everywhere, what a
legend). I think this idea of a unified simulation is very exciting, especially
since the paper that I presented on (the Octree Fluid simulation paper) had very
complex ideas/data structures for accounting for fluid/solid fluid/area
fluid/fluid interfaces. Again, a flexible framework with constraints seems to be
a good choise for simulation here.

The signed distance function collision algorithm was interesting, Max is
planning to just project the velocity and use the built-in ray tracer to due
collision detection, but I'm wondering if a shader with SDF-based collision
would improve both computational performance as well as the fluid render
quality.

The results from the unified particle physics paper are very compelling to say
the least, I've gotta say I'm a fan of Matthias Muller's work :D

### Lecture 9: Mini-Project 1
I worked with Vaishnavi Mantha for Mini-Project 1. We implemented 2 walk cycles
in Maya and manipulated mocap data to do 2 walk cycles as well.

[Presentation](https://docs.google.com/presentation/d/1uEzvJX7l8llxU9FsBGPgvWK5CkDQP1jMyTQbVxE1aos/edit?usp=sharing)

### Lecture 8: Motion Matching
I've always been quite skeptical of the concept of motion matching. A similar
concept in robotics is reinforcement learning for motions, i.e. training a
neural network to learn a policy for robotic motion. Often times it fails due to
the high-dimensionality nature of the state space.

https://montreal.ubisoft.com/en/introducing-learned-motion-matching/

The main idea of this motion matching paper is that they only look up the relevant
animation features and use the Decompressor neural network to extract the pose
rather than doing a lookup into the pose database.

One thing that I liked about this paper is that they did leverage IK for their
character animation, rather than entirely relying on feature matching.
"We add 47 new joints to our character to include hands and fingers, and add
around 30 new styles of locomotion to our data set" definitely checks out, and
I'm glad Ubisoft did their due diligence to trying to mimick such complex
motions.

Overall this paper was quite impressive and I was especially impressed by the
amount of complexity involved. I still saw some artifacts in their video demos,
but I'm definitely curious on where researchers can go from here to make motion
matching even better.

### Lecture 7: Paper Session I
#### Motion Tracking
Sort of a pedantic note, but it seems like a lot of Facebook AI research is just
chaining a bunch of neural networks together with good data and a large amount
of compute. Regardless, the results are quite impressive, and the video demo is
certainly very compelling.

#### Stop Motion
Stop motion is pretty cool, especially since it does away with the production
costs of having to render every frame. I'm concerned about the visuals of the
seams between different 3D printed parts, though this is addressed in the paper.
Maybe some sort of nifty post-processing effects specifically for this problem?

#### Motion Graphs
Not too many thoughts here, results weren't that compelling.

#### Motion Retargeting
General idea here is to decouple shape from motion, i.e. neural compression
towards a generalized simplified primal skeleton. Pretty basic idea, pretty cool
results.

### Lecture 6: Rigging & Skinning
Today we looked at some recent advances in "smart" skinning. We took a look at
RigNet and NeuroSkinning, both recent papers using learned methods to do
skinning.

It seemed to me that RigNet was simply using BoneNet and MST to come up with
the skeletal structure, and then using GMEdgeNet to do the rest of the heavy
lifting. The main challenge of rigging is skinning weights, so I'm wondering
if this approach could be modified such that an artist defines the skeleton
(i.e. takes the place of BoneNet and MST) and just have a multi-level GMEdgeNet
inference scheme to predict the skin weights.

We also took a look at NeuroSkinning, a SIGGRAPH 2019 paper. We didn't go too much
into detail with the technical aspects of this paper, but one thing I noticed
was that the models they were working with had distinctively complicated,
flowing cloth around the 3D character body. It seems like learning-based
approaches work well to approximate high-dimensional character deformations, so
I'm wondering if this paper looked at applying their deep graph networks to
"simpler" models.

We then touched base on a high-level overview of skinning methods, i.e.
physics-based, example-based, and geometry-based skinning methods. I am already
familiar with linear blend skinning (LBS) and dual quaternion skinning (DQS)
from my 3D animation class as wellas 15-462, but one thing I noticed was that
these 3 classes of methods also appear in robotics. Definitely really cool that
there is so much overlap between robotics and comptuer graphics.

### Lecture 4 & 5: Inverse Kinematics (cont.)

Today we covered more inverse kinematics papers. Two main papers that stood out
to me were FABRIK and Mesh IK.

For FABRIK, Instead of finding rotation matrices for each
joint angle to calculate joint positions, FABRIK instead finds the joint positions
by solving the inverse kinematics problem as finding a point on a line. It was
impressive to me that FABRIK could simultaneously by 10x faster than CCD and
1000x faster than Jacobian methods while producing seemingly good results. On a side note, it seems
to me that the trend of inverse kinematics papers that we've been covering in
this class is steadily pointing towards those that don't have to calculate the
Jacobians explicitly.

For Mesh IK, I found the idea of learning to deform meshes without rigs super interesting. Having done 3D animation and
more specifically rigging and weight painting, *correct* deformation of a 3D
mesh has always seemed very challenging to me.  Reinforcement learning and other
learning-based techniques are also being used in 3D animation, namely to generate
realistic character motion and as motion controllers. I'd be interested in a
generalized learning based approach to inverse kinematics, since I would imagine
that the deformation characteristics of 3D characters don't vary too much within
a certain style of animation.

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
