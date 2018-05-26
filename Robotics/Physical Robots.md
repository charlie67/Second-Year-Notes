# Physical Robots
----
[TOC]

##Locomotion

Locomotion

* Movement 
* The ability to move from one place to another

###Stability
* Number and geometry of contact points
* Centre of gravity
* Static/dynamic stability
* Inclination of terrain

###Characteristics of Contact
* Contact point/path
* Angle of contact
* Friction

###Enviroment
* Structure/medium 
  * e.g. Water, air, type of ground



## Wheeled Robot Systems

![](https://images.charlie.to/19-04-36-24-05-18.png)

Wheels can have lots of different properties

###Standard wheels
  * Simply driven
  * Steered so that the wheel direction can be changed to steer the robot 
###Caster wheels
  * Help with the stability of the system 
  * Can cause significant drag
  * Can stop it turning in particular circumstances where it's been caught on something
###Sweedish
  * Allow you to turn on the spot
  * Also called omnidirectional wheels
###Spherical wheel
  * In joysticks
  * office chairs

All of these can be motorized or steered

###4 Wheeled Systems

Unless you are on very bumpy terrain then this provides a very stable platform

Your choice of wheels and they're position can have a verry significant effect on how well your vehicle moves

![](https://images.charlie.to/19-06-30-24-05-18.png)

![](https://images.charlie.to/19-07-07-24-05-18.png)

![](https://images.charlie.to/19-07-26-24-05-18.png)

### 3 Wheeled Systems

![](https://images.charlie.to/19-07-40-24-05-18.png)

![](https://images.charlie.to/19-08-00-24-05-18.png)



### 2 Wheeled Systems

![](https://images.charlie.to/19-08-44-24-05-18.png)



### 6 Wheeled Systems

![](https://images.charlie.to/19-09-02-24-05-18.png)

### Tracked Robot Systems
* Can turn on the spot
* Move over rough terrain

### Wheeled Robot Systems
* Most common mobile robot type:
* Mechanically simple
* Easy to control
* Statically stable if more than 2 wheels
* Different wheel configurations
* Useful on solid terrain
* Rough terrain requires bigger wheels



## Legged Robot Systems

* Useful for working in our enviroments
* Advantages 
  * Adpaptable and manoeuvrable over rough terrain
  * capable of crossing pits and hole
* Disadvantages
  * Use a lot of power
  * Mecanicaly complex
  * Legs must be capable of sustaining all or part of the robots weight
  * difficult to control

### 2 Legs

They can only be staticly stable within limits, no dynamical stability and must keep servoing while standing still

#### Static (stable) walking

* Projection of the centre of gravity on the ground always inside the foot support area
* Always in a stable equilibrium
* Not biologically plausaible
* Control first, morphology second
* Low energy efficiency
* Better manoeuvrability because they're designed for our world

####Dynamic (stable) walking
* Projection of the centre of gravity on the ground can be outside the foot support area
* Mostly not in stable equlibrium
* Biologically plausible
* Morphology and its dynamics is more important than control
* Energy effciency is high
* Weak manoeuvrability they can't really take steps

### 4 Legs

* 4 legs but only two motors
* Reduces control complexity
* Static stable during standing and walking
* Synchronisation and de-synchronisation generate different gait pattern which allows change of direction

### Legged Robot Systems
* Hexapod -> static stable during walking
* Reduces control complexity
* Many possible combinations of synch- and desynchronisation -> various gait patterns
* Useful in rough terrain 



### Flying Robot Systems

* Large variety from adapted remote controlled helicopter to balloon and beyond 
* Difficult to engineer 
* Usually custom built 
* Complex sensor requirements 
* Usually no static position! 
* Affected by the weather 
* Useful in difficult to access and hostile areas
* As soon as you lose control the robot will fall to the ground
* There is not staticaly stable position



## Biologically Inspired Robots

* Fish
* Snakes
* Cockroaches
* Fleas
* Made out of biologically inspired materials 
  * They can be bend etc...



## Autonomous Sailing

* Long-term missions 
* Crossing the Atlantic ocean 
* Behaviour switching determined by battery-level and weather conditions 
* Biologically inspired control strategies (e.g. immune system, emotions)