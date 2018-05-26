# Components of Embedded Systems

----

[TOC]

## The Basics of Selection

* Microcontroller
  * A lot of the hardware depends on the capability of your microcontroller
* Input and output
  * Sensors
  * Communication
  * HCI
  	* Human computer interaction
* Power
* Cost
* Availability
  * If you want a whole production line then you want to choose something that is readily available
* Reliability
  * Don't want something that constantly breaks



### Functional Requirements

* What you want the system to be able to be able to achieve
* Battery powered? 
  * Do you need to carry it in your pocket, does it need to be portable 
    * If so needs a battery
* Wireless communication, wired in, stand alone?
  * What range if wireless
*  Local or long-range comms? 
* Human user? 
* Real-time? 
* Sensors? 
* Data processed/saved? 
* Actuators? 
* Firmware updates?

### Which microcontroller?

* Depends on a lot of different variable
* Budget
* Functional requirements 
* Need for a breakout/development board 
* Specialised versus multi-purpose 
* Size 
* Number, types and compatibility of ports 
  * How many pins you have
  * What types they are
* Power, voltage 
* Programming (programmable or pre-programmed)
* A good answer can be 
  * I'm not sure yet so i'll get a multipurpose one, even if it's more expensive and not as power efficient


### Input/output 
* Physical pins
* Digital and/or analogue
* Voltages (again!)
  * How many volts the pin outputs power at
* GPIO
* Specialised ports
* Multi-usage ports
* Enable or power devices
  * How much power the pin can provide and how much your item needs
* Long-range IO (RF, WIFI)
* Look at the pinout to find out more information for your microcontroller

### Which power

* Batteries or mains?  Often decided for you (application)
* Evaluate power consumption 
  * When the microcontroller starts it might draw lots of power for startup procedures
* Usage pattern 
* Current needs (remember to look at typical and peak) 
* Voltage (may need to regulate to different values) 
* Weight 
* Safety 
* Cost

### Which sensors and actuators

* Type decided by the application 
* Which specific one depends on all the above 
* Also depends on usability
* Read the data sheets for the sensor to see its actual specs and infomation
	* Will also list information on how the sensor operates and how it works internally


### Storage
* Secure Digital (SD) cards
  * Cheap
  * Large capacity (64GB)
  * Small (even smaller!)
  * Lightweight
  * Removable
  * Slow to write, faster to read
* Compact Flash (CF) card
  * Bigger, faster, more expensive
* Hard disks (microdrives)

### Communications 

* Cabled
*  Radio (RF): bluetooth, GSM/GPRS, WiFi, bespoke 433MHz, etc. 
  * GSM/GPRS are mobile phone networks and because of the infastructure available they are very long range
* Infra-red 
* Sound 
  * Multiple protocols 
  * Morse code
* Integrated circuits for all most of these 
* Software libraries for most of these 
* Consider the power budget!
  * Communication is very expensive in terms of power

## Building it

* Try it first either using a breadboard or a stripboard

![](https://images.charlie.to/11-07-57-25-05-18.png)

### Proper Printed Circuit Board (PCB)
* This is the smae pricnipal as a stripbaord except you create the PCB and soler the lines in 
* Software to draw it
* Hardware to make it
	* Mill it
	* Etch it 
* Expensive to make one off versions, however the costs go down with increased production

### Fix it
* There will still be bugs
* Software bugs are "easy" to fix 
* Hardware bugs can be fixed too, but generally not so easy
	* Physically changing the board
	* Need to destroy or create new connections
	* Add new wires or destry old wires



## Connected Communication

### Multiple ways of communication
* Connecting sensors to the microcontroller
* Local microcontroller to microcontroller
* Vairety of serial mechanisms
* Parrallel communications also exist but they're old and slower

###UART
* Fairly generic, dosen't specify much
* Universal Asynchronous Receiver Transmitter 
* Simple point to point, two wire interface (TX, RX)
*  Basically a shift register 
  * Generates start bit, 8 data bits (usually), stop bit 
  * Line held high when not in use 
  * Once a start bit is detected a bit sequence is transmitted and the receiver samples the input at appropriate time based on the clock (baud) rate. 
* Doesn’t define external signals or voltage levels (additional circuits may be needed) 
  * E.g. RS232, RS422, IrDA, Bluetooth Serial Port Profile 
* Also USART (synchronous, requires separate clock signal)

###RS232

* Very reliable
* A very old serial standard 
* Originally designed to connect terminals to mainframe computers 
* Quite a few pins used
*  Often on 9 or 25 pin ‘D’ type connectors Minimal 3 wire configuration can be used 
  * Very rare to still see 
  * Replace by the same protocol over USB
* Can cover large distances
* Various fixed speeds: ‘baud rates’ (e.g. 1200, 9600, 115200) 
  * Runs in bits per second
* Voltages higher than chip logic so special chips often used to interface between devices
* Threshold used to see if the voltage is high or low

###I^2^C Bus

* Inter-Integrated Circuit 
* Used for the components on a motherboard
* Designed by Philips in the early ’80s to allow easy communication between components which reside on the same circuit board 
* 100 kbit per second 
  * Also 400kbit/s fast frame mode
  * And high speed 3.4Mbit/s version 
* Only two bus lines are required 
* No strict baud rate requirements (c.f. RS232), the master generates a bus clock 
  * So you don't need to agree on a rate beforehand 
* Simple master/slave relationships exist between all components 
  * Either one can be master or a slave
  * Any master can get data from a slave
  * Each device connected to the bus is software-addressable by a unique address. I2C is a true multi-master bus providing arbitration and collision detection.

![](https://images.charlie.to/11-34-13-25-05-18.png)

* SDA and SCL pull up the voltage to get them to the high voltage
* The the master wants to talk so the master pulls down the lines while the clock is high
* This is a signal that syas you are about to start transmitting
* The master then generates a clock signal going high to low to high to low ...
* The clock is then kept high and the data is bought high as well
* This is the stop signal
* The master can address data to individual slaves

### SPI

* Serial Peripheral Interconnect 
* Full duplex 
* 10Mbit/s
*  4 wires needed 
* Data flow controlled by master with a clock (SCLK) and selecting a slave (SS or CS) 
* Data sent from the master to the slave on MOSI (or SDI) and received from the slave on MISO (or SDO)
  * MOSI is master out slave in 
    * Data from the master to the slave
  * MISO is master in slave out
    * Data goes out of the slave and into the master
* Various possible configurations

![](https://images.charlie.to/11-46-56-25-05-18.png)

* Independent
  * The master sends data to one slave that it can select
  * The slave can only send data to the master
  * The master can talk to loads of slaves in one go
    * Depending on the pins
* Daisy Chained
  * The master talks to one slave which talks the other slave
  * The data all travels around

###CAN
* Controller Area Network
* Widely used in automotive industry
* Multi-layer message based protocol
* Much larger distances than circuit board
* True network with priority messaging, robust (protocol and hardware)
* Complex and expensive to implement
* Very expensive but very robust
* Serveral standards
* Implementation defined by the devices you're using
* Priority messages can be used

###USB
* Universal Serial Bus
* General purpose mechanism to connect peripherals
* Relatively complex (software stack and transfer protocols)
* Can supply current (500mA for USB 1, up to 5A for battery charging)
* Standard connectors (many standards ;-)
* Robust against mistakes
* Vendor and product ID required
  * So that when you connect your product it can advertise itself
* Some microcontrollers provide the required hardware
* Can run over protocols over USB
  * RS232 

