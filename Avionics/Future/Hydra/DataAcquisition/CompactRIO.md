---
title: uoDAS
description: 
published: true
date: 2022-10-21T02:52:44.458Z
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

## Components
1. **Controller**
https://www.ni.com/en-ca/shop/hardware/products/compactrio-controller.html
- runs NI **linux** RTOS
- Arm or intel processors up to 2GHz clock speed

- **SSH** login capable, https://knowledge.ni.com/KnowledgeArticleDetails?id=kA03q000000YHpxCAG&l=en-CA
- has also web configuration and monitoring page

- can be programmed using python, c/c++, .NET using **nidaqmx**
1. https://www.ni.com/en-ca/support/documentation/supplemental/21/using-ni-daqmx-in-text-based-programming-environments.html#section-114540073
1. https://www.ni.com/en-ca/innovations/white-papers/13/c-c---embedded-system-design-tools.html

- API endppoint can be created using labView, https://learn-cf.ni.com/teach/riodevguide/code/rt_web-service-host.html

- cost 6,820 to 15,710 CAD

- RAM: 4 to 16 gb
- comes with integrated slots(4 to 8). ie serial ports
- compactRio board is connected to main computer using usb-c cable
- can be connected to network using ethernet cable and managed remotely using Labview. https://knowledge.ni.com/KnowledgeArticleDetails?id=kA03q000000x2HMCAY&l=en-CA


2. **Chassis**
- where you connect your modules to extend.

3. **Modules**
> I/O modules contain isolation, conversion circuitry, signal conditioning, and built-in connectivity for direct connection to industrial sensors/actuators. 
https://www.ni.com/en-ca/shop/compactrio/compactrio-modules.html

## Modules we might need
A good explanation and overview on how to use CRIO with analog sensors can be found at : https://www.youtube.com/watch?v=SJo7lqZgU3U&list=PLkS1F9cM-fqBIVntkvQme0nC_xUILWCam&index=7
It is a youtube series on a robotics channel but kinda does the same thing as us: get analog data from sensors, convert it, activate actuators, ...
`*Watch it*`
1. **Analog input NI 9201 or similar**
- This module will be attached to the chasis and will take input from the sensors
- Need a breakout board since it serial port(should come with the cRIO). The breakout booard allows the connection of 8 devices(analog inputs) on the module
***Helpful links:*** 
- https://www.ni.com/en-ca/support/model.ni-9201.html
- https://www.apexwaves.com/modular-systems/national-instruments/c-series/NI-9201?matchtype=p&network=g&device=c&keyword=ni-9201&campaign=17954270372&adgroup=145453977291
2. wireless modules
since we need data acquisition in real time, we may use a custom made radio like previous rockets or switch to the cRio wireless module.
ther are 2 options: using a cRio and adding a wireless module to the chasis. second option is purchasing a cRio with an integrated builtin wifi module.
- https://www.ni.com/en-ca/support/documentation/supplemental/08/ni-wi-fi-daq-frequently-asked-questions.html
- https://shop.sea-gmbh.com/en/SEA-9719-802.11p-Communication-Module-Configuration/60000090-CFG (price: $2,700)

## Compact DAQ vs Compact RIO
Simply put, cDAQ is smaller but requires a computer to operate while CRIO has  a Linux RTOS.
- https://www.wiresmithtech.com/articles/what-is-compactdaq/


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


