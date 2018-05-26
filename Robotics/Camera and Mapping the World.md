# Camera and Mapping the World

----

[TOC]

##Computer Vision
* Analyse images to extract infomation about the world
* Tries to mimic biological vision
* Very difficult problem

##Cameras
* 2D array of light
* Several technologies (CCD, CMOS)
	* CCD is mostly dead and  most camera are CMOS
	* There are a bunch more sensors that try to mimic biological beings
*  A huge variety of lenses
	* Narrow field of vied
	* Fisheye

##Image processing/Computer Vision
* Extract image features corresponding to world events
* Detect specific objects or simpler structures
* Estimate the 3D structure of the world (from motion, stereo, etc.)


##Mapping the World

Building maps can be useful

###Different Types of Map

####Occupancy Grid
* Regular grid
* Each cell represents an area of the world
* Each cell quantified with a number:
	* binary: occupied or not
	* continuous: “probability” of occupancy
* Trade-off between size, resolution and amount of data
* It looks like a drawing of what is around you


#####Building an Occupancy Grid

* Proximity sensor gives us the distance to the nearest object in a given direction
* The corresponding cell can be populated if we know where we are in the map
* Repeat the process for multiple sensors and/or robot positions

![](https://images.charlie.to/16-30-40-26-05-18.png)
![](https://images.charlie.to/16-30-55-26-05-18.png)
![](https://images.charlie.to/16-31-18-26-05-18.png)

##### Better Occupancy Grids

* Elfes, Using occupancy grids for mobile robot perception and navigation, 1989
* Probabilistic model of the sensor readings
* Used to update the probabilities of all cells, occupied or free
* Sensor fusion possible

##### Problems

* Can’t grow, or difficult to do
  * Once the map has been built you have to redo everything to expand the area
* No idea of object, only of there being something or not
* Can’t easily be updated, apart from modifying the probabilities
* Large amount of data or low resolution
* Need to know the position of the robot
* Depending on the sensor used, it can take a long time to populate
* Objects could move and then you'd have to update your map 

#####Vector Based Representation
* Objects positioned on the map
* Can be high level objects or just simple structures
  * High level is a table or chair etc...
  * Simple is cubes triangles etc...
* Objects can be built from the accumulation of localised information (e.g. walls from many points)
  * Robot moving along a wall can eventually say there is a wall over there
* Can be dense or sparse
* Can be expanded and modified



#### Simultaneous Localisation and Mapping (SLAM)

* Exploits vector-based maps and the possibility of representing uncertainty in the position of thing
* Chicken and egg problem: building a map and finding where we are in the map at the same time Uses a “filter” to keep track of the state of the system and improve it based on observations
  * state: pose of the robot and of landmarks
  * observations: seeing landmarks

