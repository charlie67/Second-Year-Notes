# Powering Embedded Systems

----

[TOC]

## Basic Electrical Concepts

* Voltage
  * Volt (V)
  * Potential difference
  * Electromotive force (EMF) of an electrical generator
  * Gives you the electromotive force of your circuit
  * How hard the electricity is pushing around your circuit
* Current
  * Ampere (A)
  * Symbol I
  * Flow of electrons
* Analogy with water
  * Height of a waterfall and flow of water in a pipe
* Power
  * Unit watt (W)
  * How strong the electricity in your circuit is
  * P = V * I
  * 1W = 1A at 1V
* Energy
  * Unit: Joule (J)
  * Amount of power used
  * E = P * t
  * 1J = 1W per second

### Examples

* How much current in a 60W car headlamp? 
  * Car battery 12V nominal
  * P = V*I
  * I = P/V = 60/12 = 5
* How much current in a mains 60W bulb? 
  * Mains 240V nominal
  * P = V*I
  * I = P/V = 60/240 = 0.25



### Battery Characteristics

* Charge
  * Coulombs (C) 
  * C = I × t 
  * 1C = 1A for 1s 
  * Usually given as Ah or mAh
  * How many Colulombs in a 1mAh battery
    * 1*10^-3^  \* (60\*60) = 3.6
  * How long would a 800mAh battery last delivering:
    * 0.8A
      * 1 hour
    * 400mA
      * 2 hours
    * 1.6A
      * 30 minutes
    * 800 mAh in 0.8 Amps for an hour
* Charge and discharge rate
  * Given in ‘C’: 1C, 2C, 30C, etc.
  *  C notation as documented in the standard IEC_61434 
  * C (A) = capacity (Ah) / 1 (h) 
  * 1C is typically the capcaity in amp hour divided by 1 hour
  * 1C means that you can charge or discharge your battery in 1 hour
  * 2C means that you can charge or discharge your battery in 30 minutes
  * Nothing to do with Coulombs
  * How long does it take to charge a 800mAh battery at 1C, at 2C?
    * 1 hour 
    * 30 minutes
  * Internal resistance
    * Reduce the effective voltage as current increases

### From cells to batteries

* Only combine identical cells
	* This is important, bad things can happen
* Series
  * voltage: sum of voltages 
  * current, same in each cell 
  * capacity: same as each cell
* Parallel
  * voltage: same as each cell 
  * current: sum of all currents 
  * capacity: sum of all capacities

![](https://images.charlie.to/14-06-11-25-05-18.png)
Top is series, bottom is parallel

## Batteries

* Cell, collection of cells 
* Primary cell (non-rechargeable) 
* Rechargeable 
* Many different chemistries

### What makes a good battery

* Energy density 
  * "Store lots of energy"
  * Per unit of mass?
  * Per unit of volume?
* "Long lifetime"
  * Number of charge cycles
  * shelf-life
    * How long it can be left sitting around for without losing charge
  * Resistance to charge cycle abuse
* Safety
  * Simple/safe charge characterisitce and storage regimes
  * Short-circuit behavious
  * Mechanical resilience
  * Enviroment impact/poisoning capability



### Batteries are not perfect

* You don’t get out everything you put in: 
  * Self-discharge 
  * Peukert’s law: capacity depends on discharge rate 
  * Internal resistance
    * Often increases with age and in some cases each charging cycle
    * A high internal resistance means that if you draw a lot of current than you have a high voltage drop inside the battery and therefore you have a voltage drop in your circuit
  * Coulometric charging efficiency: ratio of charge coming out and charge coming in 
    * Below 100%
    * Cells do not retain all of the charge provided 
    * Fast charge generally less efficient 
* Why? 
  * Battery chemistry



### Battery Chemistry

* Two electrodes made from two different substances, often metals 
* Transport medium between, usually a liquid/gel 
* The two electrodes need to be capable of releasing electrons and creating ions in the transport medium 
* The ease of release of electrons from an electrode is different for different substances

#### Galvanic Series

![](https://images.charlie.to/15-05-37-25-05-18.png)

* Arrange the substances in order of “ease of release of electrons” 
  * Potential to release an electron and form a positively charged ion 
* Choose two from far apart for higher voltage 
* Voltage depends on galvanic potential and solution 
* Zinc and Copper = 1.1V
* Nickel and Cadmium = 1.2V
* Silver and Zinc = 1.6V

#### Daniel Cell: a Simple Wet Cell
![](https://images.charlie.to/15-10-15-25-05-18.png)

* You have two containers that are linked by a salt bridge
  * Literally a tube with salt in it
* The right hand one has a copper electrode
  * The liquid in there has a lot of copper ion in
  * This means that it has a high positive charge
  * It's saturated which means taht you can't put any more in
* The left side has a weak zinc suplhate solution 
  * Weak so not many in there
  * The zinc electorde will disolve and the zinc will seperate with the zinc disolving into the zinc sulphate solution, in this process the zinc will turn into zinc ions and electrons
  * While this is happening the copper will stick to the copper cathode
* The zinc electrode will get smaller and smaller while the copper on egets bigger
* The battery is flat when:
  *  The zinc sulfate is saturated
  * The zinc electrode is gone so there is no circulation anymore
* All about chemical reactions 
* Both metals want to “dissolve” (oxidation-reduction) in the solution thus releasing electrons 
* Zn is less noble (anodic) than Cu so will tend to release more electrons while Cu will capture more 
* Connecting the two electrodes makes electrons flow from Zn to Cu 
* The sulphate ions migrate to release more electrons at the anode (by allowing the Zn to continue to dissolve) from the sulphate released at the copper electrode 
* Concentration in sulfate around Zn increase while it decreases around Cu

####Charging the Cell

* Reverse the process by forcing current eh other way
* "Rebuild" the Zn electrode and "dissolve" the Cu into the solution
* Re-balance the sulfate concentrations


####Lead-acid battery
![](https://images.charlie.to/15-19-49-25-05-18.png)

* Lead and lead sulphate electrodes
* Sulphuric acid solution as the transport medium (electrolyte) as liquid or gel
* Electrodes arranged as flat plates seperated by liquid
* Thich plastic container to dangle the cells in
* Can produce a huge amount of current
* Very heavy
* Slow to charge
  * 12-16 hours
* Fully charged: 2.1–2.13V per cell
* Fully discharged: 1.97–2.0V per cell
  * Both electrodes are lead sulphate
  * Electrolyte becomes mostly water



#### Nickel-cadmium

![](https://images.charlie.to/15-24-38-25-05-18.png)

* Rolled up nickel and cadmium sandwich 
* Separator between electrodes
*  Potassium hydroxide solution transport medium 
* Often rolled up into standard AA (or whatever) cylindrical form factor 
* Fully charged: 1.3–1.4 V per cell 
* Fully discharged: 0.9–1.0 V per cell 
* Being replaced by NiMH — mostly because cadmium is nasty stuf

####Nickel-metal Hydride

![](https://images.charlie.to/16-34-54-25-05-18.png)

* NiMH battery use a hydrogen-absorbing alloy for the negative electrode instead of cadmium
* NiMH cells can have two to three times the capacity of an equivalent size nikel-cadmium cell
* Volumetric energy density is lower and self-discharge is higher than lithium-ion
* They have a much higher energy density then nickel-cadmium
* They will self discharge very quickly
* They will degrade with time

####Lithium Ion
* Lithium ions move from anode to cathode during discharge
* Various different chemistries are used, with different performance
* Non aqueous electrolyte
* Can easily be manufactured in various shapes
* Low self-discharge
* High energy density
* High recharge rate (compared to previous chemistries), typically 1C but could be higher
* Relatively high internal resistance compared to NiCd and NiMH
* Each cycle causes deposits to form in the electrolyte that reduce capacity and increases internal resistance
* Chemistry degrades with time and is temperature dependant
* Damaged by over-discharge
  * some now contain special circuits to prevent this
* Can be dangerous if incorrectly charged or handled
* Series connected cells forming a battery may need  “balancing”
   * When charaging you need to ensure that one dosen't overcharage and they charge at the same rate
* The transport layer is very often a gel or sometimes a solid
  * It is never a liquid
* Very dificult ro revive if totally out of charge
   * This is why they have a circuit board to monitor the output voltage

#####Lithium Polymer

![](https://images.charlie.to/16-49-02-25-05-18.png)

* LiPo
* A Lithium ion battery in a polymer pouch
* Gelled liquid electrolyte
* Lighter and can be made in a variety of shapes and sizes
* Particularly useful for applications where weight is of concern
* Can be charged at 3/4C with no problem

#####Lithium iron phosphate

* LiFePO~4~, another Lithium ion chemistry
* Claims very long life (10 years)
* Slightly lower energy density than other Lithium ion chemistries
* High discharge rate (higher then many other Lithium ion chemistries)
* 2/3 the weight of lead acid for the same capacity
* Low self-discharge
* Can recharge in an hour
* Safer than other Lithium ion chemistries
* 3.2V per cell
  * Can replace a 12V lead-acid battery
  * Much higher energy density than lead-acid

#### Primary Cells

* In increasing order of energy density
* Zinc-carbon: now dead
	* About 20 years old 
* Alkaline: still used a lot
* Lithium: for special applications such as watches, computer clock backup, etc.
* ![](https://images.charlie.to/16-58-22-25-05-18.png)

####Battery Discharge rates
![](https://images.charlie.to/17-00-39-25-05-18.png)
* If your company needs 1.5V then as soon as you start running it won't work 

####Battery Charging

* Different methods depending on the chemistry
* Lead-acid and Lithium-based batteries: Constant Current/ConstantVoltage ( CC/CV)
  * First constant current until maximum voltage reached
  * Then constant voltage until current is null.
  * A constant current is pushed into the battery to reverse the chemical reaction
  * You monitor the voltage and when the voltage is at the maximum you switch  to a constant voltage
* Nickel-based batteries: constant current with floating voltage
  * Stop after a while! (typically low current)
  * Stop when too hot (or temperature increasing suddenly)
  * Stop when voltage drops (typically higher current)
  * Combination of these

#### Example 

* How long can you run a computer for on a  60Ah 12v car battery

* 190W power consumption for a PC
* I= P/V
* 190/12 = 15.83A
* 60/15.83 = 3.8
* Run through inverter (≈80% efficient?)
  * Because the battery outputs DC voltage and the computer needs AC
* Car batteries don't like deep discharge so this will effect the lifetime of the battery

### Usage Pattern

* Not always on, or running at full power
* Worst case, best case, typical, peak (current but also speed of producing regulated power)
  * Need to consider all the things that could happen while it's running
* Expected operating cycle
* Estimates and approximations!
* Consider the power source: wind, solar, batteries, mains
  * Need to consider what your power source can deliver
  * If you're using batteries they will discharage or reach there end of life
  * If you're using wind/solar then you might need to trade off current for how much power your solar panel or wind brings in



### Power Management

* Many obvious things you can do:
  * reduce power
  * CPU frequency
  * sleep
  * don’t power things that are not used
  * choose the right components
* Some not so obvious:
  * only use electricity when you can afford it
  * trade off usage and survivability
  * if you can’t do something, don’t try harder but try later



## Power Scavenging

* Theres lots of power around us that we could tap into and use
* Antenna Vibration and movement 
  * kinetic, piezo-electric, biomechanical 
* Photo Voltaic (PV)