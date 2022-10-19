---
title: uoDAS
description: 
published: true
date: 2022-10-19T04:03:09.876Z
tags: 
editor: markdown
dateCreated: 2022-10-15T16:31:23.915Z
---

# CompactRIO
>  **CompactRIO** systems feature a controller with a processor running a Linux Real-Time OS and a chassis that contains a user-programmable FPGA
{.is-info}

## Glossary
**compactRIO(cRIO)**: compact Reconfigurable IO 
**FPGA**: Field-programmable Gate Array. 
- An integrated circuit that you can program to implement a certain circuit or logic design(schematic).
- They are flexible and can be usded to implement various systems
- programmed using Hardware description language(HDL) i.e Verilog HDL
- perfomant since they allow parallel processing
(video explanation)https://www.youtube.com/watch?v=WY-F3knih7c

## components
1. **Controller**
https://www.ni.com/en-ca/shop/hardware/products/compactrio-controller.html
- runs NI linux RTOS
- Arm or intel processors up to 2GHz clock speed
- cost 6,820 to 15,710 CAD
- RAM: 4 to 16 gb
- comes with integrated slots(4 to 8). ie serial
- compactRio board is connected to main computer using usb-c cable
- can be connected to network using ethernet cable and managed remotely using Labview. https://knowledge.ni.com/KnowledgeArticleDetails?id=kA03q000000x2HMCAY&l=en-CA


2. **chassis**
- where you connect your modules to extend.

3. **Modules**
> I/O modules contain isolation, conversion circuitry, signal conditioning, and built-in connectivity for direct connection to industrial sensors/actuators. 
https://www.ni.com/en-ca/shop/compactrio/compactrio-modules.html

## Modules we might need
A good explanation and overview on how to use CRIO with analog sensors can be found at : https://www.youtube.com/watch?v=SJo7lqZgU3U&list=PLkS1F9cM-fqBIVntkvQme0nC_xUILWCam&index=7
It is a youtube series on a robotics channel but kinda does the same thing as us: get analog data from sensors, convert it, activate actuators, ...
`*Watch it*`
1. **Analog input NI 9201 or similar**
- This is a module to be attached to the chasis and takes in input from sensors
- Need a breakout board since it serial port. The breakout booard allows the connection of 8 devices on the module
***Helpful links:*** 
- https://www.ni.com/en-ca/support/model.ni-9201.html
- https://www.apexwaves.com/modular-systems/national-instruments/c-series/NI-9201?matchtype=p&network=g&device=c&keyword=ni-9201&campaign=17954270372&adgroup=145453977291

## compact DAQ vs Compact RIO
Simply put, ca is smaller but requires a computer to operate while CRIO has  a Linux RTOS.

## Setup
comes with:
1. cRio screw driver
2. getting started flyer
	-> https://learn.ni.com/pages/getting-started
3. CD with drivers. // can be downloaded online

software to install:
1. LabView
2. LabView RT
3. LabView FPGA
4. Compact RIO device drivers i.e NI CompactRIO


