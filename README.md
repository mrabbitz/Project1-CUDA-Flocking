**University of Pennsylvania, CIS 5650: GPU Programming and Architecture,
Project 1 - Flocking**

* Michael Rabbitz
  * [LinkedIn](https://www.linkedin.com/in/mike-rabbitz)
* Tested on: Windows 10, i7-9750H @ 2.60GHz 32GB, RTX 2060 6GB (Personal)

## Part 1: Flocking Simulation Overview

In the Boids flocking simulation, particles representing birds or fish
(boids) move around the simulation space according to three rules:

1. **Cohesion** - boids move towards the perceived center of mass of their neighbors
2. **Separation** - boids avoid getting to close to their neighbors
3. **Alignment** - boids generally try to move with the same direction and speed as
their neighbors

These three rules specify a boid's velocity change in a timestep.
At every timestep, a boid thus has to look at each of its neighboring boids
and compute the velocity change contribution from each of the three rules.

The implemented algorithm for the three rules is based on [Conard Parker's notes](http://www.vergenet.net/~conrad/boids/pseudocode.html)
with slight adaptations. For the purposes of an interesting simulation,
we will say that two boids only influence each other by a given rule if they
are within the rule's **neighborhood distance** of each other, respectively.

Below are two outputs from the simulation, slowed down for easier viewing:

|25,000 Boids|
|:--:|
|![25kBoids](images/Debug_25kBoids_Coherent_100Scale.gif)|

|500,000 Boids|
|:--:|
|![500kBoids](images/Release_500kBoids_Coherent_500Scale.gif)|

## Part 2: Performance Analysis
