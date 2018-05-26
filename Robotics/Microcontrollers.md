# Microcontrollers

----

[TOC]

## Basic Definitions

* Embedded system
  * Computer system with a specific task as part of a larger system
* Microcontrollers are the central processing unit of the embedded world



## Properties

* Small
* Cheap
* Real time processing
* Highly integrated
* Quite specialised
* Power saving



## Typical Parts

* Storage
* Central processing unit
  * Control unit
  * Arthimetic/Logic unit
* Buses
* Clock (sometimes)
* Peripherals
  * Timers
  * Communication ports
  * Data processors



## Storage

### Non-volitale storage

* Storage that won't "lose" its contents if you cut the power
* Read-only memory (ROM) 

  * Obviously not read only forever because you need to write data to it to begin with, however writing is a very intensive process
* Used to store firmware or data that needs to be saved after powering down
* Erasable programmable read-only memory (EPROM)
  * Erasable with UV in totality
  * Writable with "high" volage, very slow
    * "high" voltage means a higher voltage than you normally use to access the memory
  * Not so long term storage
* Electrically etasable programmable read only memory (EEPROM)
  * Erasable down to individual words using electricity
    * Word refers to a byte or 32 bits
      * Depends on the chip
  * Limited number of writes (100,000 or more)
* Flash memory
  * Erasable in blocks
  * Limited number of writes (10,000)
  * Highly integrated and cheap

### Volitale storage

* Storage that will lose its contents if power is lost
* It's not designed to keep its data
* Random access memory (RAM)
  * Data is lost when not powered
* Dynamic RAM (DRAM)
  * Stored values need to be refreshed regulary
    * Capictors need to be recharged
  * Relatively slow
  * Cheap and high density 
  * Used as main memory
* Static RAM (SRAM)
  * Faster
  * Expensive and lower density
  * Used as cache



## Architectures

![](https://images.charlie.to/09-53-05-25-05-18.png)

### Von Neumann

* One memory space, this is used both for the instructions and the data
* The control unit controls what happens to the program 
  * Read through this data
  * Do an operation
  * etc...
* The control unit gets the instructions from the memory by sending an address and fetching the instruction at the given address
* The control unit then sends the data to the ALU and the ALU will perform an operation on the data
* The ALU can get either an instruction or data but not both at the same time
* One address space
* Data and instructions use a single bus to the processor
* Data and instructions must be accessed in turn, the “von Neumann bottleneck”
  * This makes it slow
* Addresses interpreted as either data or program instructions dependent on the context. It is possible for the program to change its own code...
  * This means it could get it wrong and write data over the program



### Harvard

* You have two bits of data one for instructions and one for data 
  * So it can get both at the same time which speeds it up
* Program and data each have their own address spaces
* Program instructions and data each have their own path (bus) to the CPU
* Instructions and data can be fetched simultaneously
* Program and data memories can be implemented differently (e.g. flash and SRAM), differ in size and can use different bus width
* e.g. 12 bit memory for instructions and 8 bit memory for data 
* Impossible for a program malfunction to destroy itself
  * Because the address spaces are seperate
* This stops compilelrs from properly working becuase a compiler is turning data into instructions which need to be saved into the instruction area 



#### Modified Harvard Architectures

* Pure Harvard can’t treat data as instructions or instructions as data... Problem for compilers, JIT compilation, etc.
* Modified Harvard architectures provide special machine operations to access the contents of the instruction memory as data
* Capability for reprogramming is generally required 
  * Special instructions and procedures to write to program memory (and data EEPROM)
  * Hard to accidentally corrupt program

## Peripherals

* Not printers!
* Timers
* GPIO ports (General Purpose Input/Output)
* ADCs (Analog Digital Converter)
* comparators
* Pulse Width Modulation (PWM)
* UARTs (Universal Asynchronous Receiver/Transmitter)
* I^2^C (Inter-Integrated Circuit)
* SPI (Serial Peripheral Interface)
* Driven by dedicated hardware or software



## Power Saving

* Sleep modes (CPU off, peripherals off)
* Idle modes (peripherals on)
* Clock speed reduction
* Internal/external oscillator
* Low voltage versions
* Many attempts at low power destroyed by the breakout board!
	* ESP8266 in deep sleep: 10µA
	* NodeMCU board: LoLin 3.5mA, Amica 18.5mA (18,500µA)
* Scavenging (later)

