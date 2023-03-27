---
title: Current System State
description: 
published: true
date: 2023-03-27T18:31:06.555Z
tags: 
editor: markdown
dateCreated: 2023-03-27T18:31:06.555Z
---

# Current System State

## General Hardware State of all avionic systems

### Issues
- Raspberry Pi - they are now crazyyyy expensive, and we are out of stock. we can't afford to fry one, and it will happen eventually. They are also way too sensitive to voltage changes and power off very easily
- Communication - We use bare TCP for inner and inter system communication - which is simple in some ways, but complex in other since we use bare sockets connection (and we need to account for things like network disconnection, timeout, multiple clients, ...)


## Data Aquisition (Sensor Suite)

#### General State Hardware State

Very Good since it has been redone, and fully working. However not everything as been tested with new software, and some stuff is still not implemented in hardware (like load/button cells)

#### General Software State

Old Sensor Suite Software was made with wrong requirements - which resulted in complex code. We do not need this anymore. However, it is still usefull to see how the code was made and arranged

A re writing of sensor suite has been succesfully attempted for the thermocouple and for controlling the heater of the tank. 

This re-write has not been attempted with the DataQ and load/button cells

#### Thermocouples

- Hardware have been tested and working
- Software with Sensor suite 2 have been tested and working
- Each theromocouple connnector still need to be checked since they had issues

#### Presure transducers over DataQ

- Implented in hardware - very clean
- Not tested at all with the new hardware. 
- Not integrated with the new sensor suite software
- Not calibrated

#### load cells/button cells

- Not Implemented in Software
- Not implemented in Hardware
- Not tested
- Not calibrated



## Control System (Fill Cart)

#### General Software State

- It works but nightmare
- Maintaining it will be longer than re-writing it - yes it's that bad
- overall not good

#### General Hardware State
- Kinda nightmare too
- Proto board of fill cart arduino is too convoluted. Something will eventually break and will be nightmare to replace or add a valve/feature
- connectors are sketchy - but somewhat working

#### Vent Valve (Solenoid)

- Gets 12V input
- Controlled by a 12V relay
- Works well - safety critical

#### Igniter
- NOT OKAY - when we power on the system it briefely turns on for 1/3s, which could temporarly heat up the thermocouple. this is due to the relay is default close in a weird state

#### Servo Ball Valves
- Right now we only have 2, but we need 3 (for run N2 tank). 3rd one could easily be integrated since hardware already exists for it (previously the main feed line used a servo ball valve)
- Connectors are sketchy but working okay
- PWM over very long wires is also very sketchy but seems to be working
- We need to 0 each valve each time we test something - hudge waste of time and high potential of breaking something

#### Main Feed Valve
- Disaster - need at least new proto board for it
- we can't easily get an h bridge motor driver for it - if we fry this one we are screwed
- Connectors are very very sketchy


## Communication System

#### General state

- Connectors for the ethernet cables are not okay at all - something will disconnect which will force us to abort the test. 
- We are using the system outside it's specs, but we hacked it in a skechy way. this has to be tested - and we need to 