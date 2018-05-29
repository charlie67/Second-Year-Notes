# Reactive Systems

----

[TOC]

## Allen

* Level 0 – Avoid Obstacles 
  * Robot does not come into contact with obstacles 
  * If approached, moves away 
  * If collision when moving, stop 
  * Otherwise sit still 
* Level 1 – Wander Around 
  * Wander without hitting objects 
* Level 2 – Explore 
  * ● Uses visual observations to select interesting places to visit

### Level 0

![](https://images.charlie.to/20-15-29-27-05-18.png)

* Sonar – takes readings, filters for invalid readings, and interprets as locations of obstacles in relation to the robot – a map
* FeelForce – sums the repulsive forces of all the obstacles
* RunAway – monitors the force result from the FeelForce module and sends a signal to the Turn module if it's significant
* Turn – receives a turn angle plus forward motion magnitude, commands the robot to turn, then passes on the magnitude to the forward behaviour and sets its own state to waiting 
* Forward – moves the robot forward, then sends a reset signal to the turn behaviour 
* Collide – monitors the map of sonar readings and if it detects obstacles ahead it sends a halt message to the forward behaviour

### Level 1 - Wander Around

![](https://images.charlie.to/20-16-52-27-05-18.png)

* Relies on the layer below, and uses data from it 
* Wander – generates a new heading approx every 10 seconds 
* Avoid – adds to the lower level behaviour – takes the force result from the FeelForce behaviour, combines it with the reading from the wander behaviour, and suppresses the runaway behaviour's output with its own output
* The Avoid behaviour subsumes the RunAway behaviour on the level below



### Level 2 - Explore

![](https://images.charlie.to/20-18-17-27-05-18.png)

##Emergent Behaviour
* The overall behaviour which is the product of the individual behaviours programmed into the robot, their interaction with each other and with the environment
* The real world is filled with uncertainty and dynamic properties
* Addional complexity of perceiving the world
* These interactions cannot be predicted, and so can produce unexpected emergent behaviour

##Subsumption Architecture

* Robustness often hardwired in and hence hard to implement 
* ● Usually custom behaviour design – takes time and has a big learning curve



### Strengths

* Hardware retargetability - can be compiled down onto programmable-array logic circuitry 
* Support for parallelism – each behaviour can run independently and asynchronously 
* Niche targetability – custom behaviours can be created for specific task-environment pairs

### Weaknesses

* Lack of run-time flexibility – limits to the way the system can be adapted during execution 
* Upper layers cannot be designed completely independently from lower but does support behaviour re-use 
* Little support for modularity