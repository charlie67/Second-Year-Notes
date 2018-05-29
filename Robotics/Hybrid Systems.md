# Hybrid Systems

----

[TOC]

## Hybrid Architectures

* Take advantage of the goal oriented deliberative systems 
* Plus the reactive systems which prove more able to deal with a changing world 
* Typically a deliberative system with interface to a reactive system 
* ● Plans based on knowledge, with the advantage of responsiveness to the environment

## Possible Hybrid Interfaces

1. Allows both systems to think they have full control over the robot's actuators (the framework mediates between the two)
2. Each system can use knowledge from the other, but a supervisor controls both 
3. The deliberative system provides information which directs the behaviour of the reactive system 
4. The deliberative system directly manipulates the structure and behaviour of the reactive control system

* Need to have a careful balance between the reactive and deliberative systems



## AuRA Example

* R. Arkin 
* Reactive component 
  * Schema-based architecture 
  * Can be used alone to control a robot reactively 
* Deliberative component is a hierarchical system based on traditional AI techniques



### Reactive Component

* Each individual behaviour represented as a schema, essentially an equation
*  Work together produce the emergent behaviour 
* Sensor information is used to calculate a vector 
  * one for each behaviour (magnitude and direction) 
* Added up to produce a single direction vector 
* Creates potential fields around obstacles (repulsors) and towards the goal (attractor) 
* There is no overall map of the potential fields Example Set of Beh
  * There is just a bunch of sensor infomation



#### Example set of Behaviours

* Make a robot move towards a goal while avoiding obstacles 
  * Avoid-obstacle: Moves the robot away from obstacles. The magnitude effected by the sphere of influence of the obstacle, and a gain value; the direction is simply away from the obstacle 
  * Move-to-goal: Moves the robot towards the goal, magnitude effected by a gain value; direction is towards the goal 
  * Noise: produces a random walk. The magnitude effected by a gain value, the direction is random

#### Motor and Perceptual Schemas

* Motor Schemas
  * control the robot's effectors 
* Perceptual schemas 
  * provide information for the motor schemas 
* For instance, 
  * the perceptual find-obstacle schema may be in operation as a robot moves around a space, 
  * if it detects an obstacle then it will instantiate the avoid-obstacle schema 
  * this will use the information about the obstacle from the find-obstacle schema to avoid it



## Trash Collecting Robot Example



* Won AAAI Robot competition
  * Team of robots collected trash and deposited into trash cans
  * The group won the competition 
  * Used assemblages of schemas



### Move-To-Trash Assemblage

* detect-red-blob: perceptual schema (looks for red trash) 
* detect-obstacles: perceptual schema (detects and tracks obstacles) 
* move-to-goal: motor schema (generates a vector towards trash)
*  avoid-static-obstacles: motor schema (generates a vector away from obstacles) 
* detect-IR-beam-broken: perceptual schema (detects when the infra red beam in the robot's gripper is broken) 
* Once the detect-IR-beam-broken is activated the move-to-trash assemblage is terminated and the next assemblage, grab-trash is instantiated

### Hierarchical Architecture

![](https://images.charlie.to/12-50-47-28-05-18.png)

* The robot was mostly reactive but had some deliberative systems to check if something went wrong
* Navigating Robot 
  * Mission planner: the highest level of command, often used as an interface for human command input 
  * Spatial reasoner: uses map information stored in memory to construct routes, e.g. can simply use A* search to search a map
  * Plan sequencer: translates each leg of the route into a set of motor schemas
* Motor schemas created by the plan sequencer are sent to the reactive system 
* These are added to the reactively generated schemas 
* ● Deliberative part not reactivated unless an error is detected