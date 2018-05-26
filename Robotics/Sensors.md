# Sensors

----

[TOC]

## Introduction

* Sensors to sense 
  * the state of the robot (proprioceptive)
  * the environment (exteroceptive) 
* Active and passive sensors 
* Absolute and relative sensors
* Sensors are
  * Noisy 
  * Of variable accuracy, repeatability and resolution 
  * Unreliable 
  * Difficult to model 
* Sensors map the world
  * Sensors can be used to know where we are in the world
  * And to map the world
  * Noise needs to be dealt with



## Proprioceptive position sensors

### Encoders

* Two types

####Shaft Encoders

* Rotating disk mounted on motor/gearbox shaft 
* Holes or slots to vary some signal (light, magnetic, etc.) 
* Counting ticks 
* Gives us the rotation of the wheel
* Can have varying resolutions which impact how precise they can be

![](https://images.charlie.to/18-21-28-25-05-18.png)


####Quadrature Shaft Encoders
* Use phase shift between two sensors
* Also measure direction of rotation
* More precise because of two sensors instead of one
![](https://images.charlie.to/18-19-41-25-05-18.png)

#### What for?

* Measuring orientation of robotic link (e.g. steering) with absolute encoder 
* Counting wheel turns 
* Measuring the pose (position and orientation) of a mobile robot



### Accelerometers

* Measure the acceleration along one axis
* 2D and 3D accelerometers
* Micro-Electro-Mechanical devices (MEMs)

![](https://images.charlie.to/18-30-19-25-05-18.png)

####What for?
* Acceleration: rate of change of spee
* Speed: rate of change of position
* Double integration of acceleration
* Changes of position can be measured, i.e. position relative to a starting point


###Micro-Electo-Mechanical devices (MEMs)

* Microscopic devices
* Mechanical parts (e.g. piezoelectric transducers used in accelerometers)
* Microcontroller to process the data
* Often offer high level interfaces


###Gyroscopes
* Measure rotational changes
* Spinning disk tends to keep its orientation
* Relative moves of the frame indicate change in orientation
* Constraining axes creates forces that can be measured
* MEM devices will give a rotation rate

![](https://images.charlie.to/18-41-30-25-05-18.png)

####What for?
* Rotation rate is integrated to get relative orientation

###Relative Pose Measurement
* Pose: position and orientation
* Measured relative to a starting value using the sensors described above
* Current value is the result of adding small changes at each step
* We can measure the pose relative to a starting point
* One of the big problems is that all the snenors are noisy to some extent and we are integrating and adding small displacements each time
* We adding more errors in as we progress by integrating

###Sensor Fusion

* Fuse the information from different sensors
*  All sensors perform differently and at different frame rates 
* Take the best from each to maintain a better estimate of the state of the system (robot) 
* Kalman filter (and many other methods)

###Kalman Filter

* State of the system at step k, given previous k − 1 steps: xˆ~k|k−1~
  * e.g. the robot’s position and orientation
* Uncertainty of the state: P~k|k−1~
  * How good or bad the value is
  * The Standard deviation
* Sensor measurement (observation) at step k: y~k~ 
* The kalman filter is essentially mantaining the state and uncertainty while you process
* At each step, iteratively:
  * predict the new state and its uncertainty using the equations that describe how the state changes 
  * update the prediction based on new sensor measurements (observations)
* Uses models of the noise of the state and observations 
* Combines them such that the state estimate is better than if only one observation was used 
* Possible to have multiple prediction and/or update steps

![](https://images.charlie.to/19-33-52-25-05-18.png)



### Inclinometer

* Measure absolute attitude of object
* Sense acceleration created by gravity
* If you're accellerating while taking the measurement then you're reading is rubbish

### Compass

* Gives absolute orientation (from North)
* Senses magnetic field of the Earth 
* Tilt and position compensation
* Can be affected by other strong magnets
  * A speaker
  * A wire with AC current
* Gives orientation with 0 being north
* This is not the same as geographic north
  * Which is why sometimes there is position copensation

### Global Navigation Satellite Systems (GNSS)

* Passive system
* Rely on triangulation from the position of satellites and distance to them
* Heading from position derivative and Doppler effect
* Various systems:
  * GPS (Global Positioning System, US): about 5m
  * GLONASS (Global Navigation Satellite System, Russia): about 5m
  * BeiDou (China): 10m
  * Galileo (Europe): about 1m (will be)
* A lot of clever signal processing to improve things
  * Differential
  * Real-Time Kinematic

### National Marine Electronics Association (NMEA) data

* Specification for marine equipment to communicate 
* Used by GNSS systems 
* Often on RS232 
* Information sent as sentences defined by the specification as characters 
* Minimum recommended: time, status, latitude, longitude, speed, heading, date, magnetic variation, checksum: $GPRMC,123519,A,4807.038,N,01131.000,E,022.4,084.4, 230394,003.1,W*6A

### Absolute Pose Measurement

* Sensors above give an absolute estimation of the position and/or orientation
* Non-drifting
* Possibly noisy and not very accurate (disturbed by external causes)

### Better Pose Measurement 

* Relative sensors tend to be more accurate but drifting and noisy
* Absolute sensors don’t drift but are not so accurate
* Combine both to get a better result
* For example:
  * Roll and tilt from a gyroscope can be stabilised by a gravity measure (accelerometer)
  * Yaw from a gyroscope can be stabilised by a compass measurement

##Exteroceptive Proximity Sensor

###Sonarr

* Acoustic signal sent 
* Listening for an echo response
* Timing tells us how far the object is 
* Timeout! 
  * If nothing is received back in a certain amount of time
* Range up to about 5m, field of view about 15◦ 
* Problems due to multipath reflections and interference
* Each sensor can interfere with another sensor if they're too close together and firing at the same time
  * The signal can bouce back and hit 2 sensors giving garbage results

###Interrupts

* Interrupt: interrupt normal flow of program by calling a specified funtion (Interrupt Service Routine)
* Normal flow is resumed once the ISR has terminated
* Guaranties on timing
* Interrupts on specific pins when something specific happens
* E.g. when the sonar echo pulse goes down, with appropriate time
  measurement

###LIDAR (Light and RADAR)

* Light (and laser in particular) can be used in a similar manner to sound
* Time of Flight (and other methods to measure distance, such as phase shift)
* Scanning of the laser beam horizontally and/or vertically (up to 360◦)
* Very power hungry, bulky and expensive
* Some can reach distances of several kilometres

![](https://images.charlie.to/15-30-05-26-05-18.png)

###Infra-red (IR)

* IR LED emits light
* Sensitive to specific motions, visual features and surfaces
* Distance measured:
  * Offset array of detectors measures distnace by tiangulation
  * Intensity of reflection is indicitive of the distance
  * If the object is further away then the value returned will be lower
* Non-linear response
* ~20cm range

###Sonar v Lidar v IR

* Cars front and back bumper sensors are sonarr
* Cars have radar to tell you if you shouldn't change lane on a motorway becuase of a car on your side
  * Radar is cheap
* Prototypes of self driving ars use lidar 
  * Because you get a very detailed view of what is around you
* However more data needs more processing

* Active are better at getting more information because you're controlling what is put out into the enviroment so they can be better at filtering out noise