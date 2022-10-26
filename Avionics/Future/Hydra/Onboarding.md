---
title: Onboarding
description: 
published: true
date: 2022-10-26T14:05:40.836Z
tags: 
editor: markdown
dateCreated: 2022-10-22T01:49:18.966Z
---

# Useful links

C++ Tutorial: http://uorocketry.wikidot.com/wiki:cpp-resources
CAN-BUS Primer: https://dewesoft.com/daq/what-is-can-bus
Intro to Microcontrollers: https://www.embeddedrelated.com/showarticle/453.php\
ASF4 Reference Manual: https://onlinedocs.microchip.com/pr/GUID-2A8AADED-413E-4021-AF0C-D99E61B8160D-en-US-4/index.html?GUID-1051C71D-4C07-406C-ACCE-BFE886294818

# Software Dev Setup
Repo: https://github.com/uorocketry/hydra

## Linux
- Clone the repo
- Install MPLab IPE (This is for programming the devices. You can download the needed device pack online)
- Install the XC32 compiler and add the bin to your PATH variable.
- Install Ninja and CMake. Apt is ninja-build and cmake.
- Install VSCode or CLion for the IDE
- Use the build script to build by specifying the device you'd like to build for e.g. ./build.sh main
## Windows
TODO

# Software Intro
## ASF4
We use a advanced software framework to handle lower level code.  
### Diagram of the advanced software framework
![asf4.png](/asf4.png)

## CAN
We use CAN technology to communicate between nodes. 
The ASF4 covers the implementation of CAN. 
### CAN Analogy
You are a CAN node and enter Starbucks wanting to order an iced coffee. 
So, you wait in line to order; this is the transmit queue and works 
on the principle of FIFO (first in first out). You're at the cash and ready to order.
The cash is the node you are talking to and other customers are also nodes. 
You tell the cashier you'd like an iced coffee and give them your name. 
Now you go over to the end of the counter to wait for your drink. 
Your order won't be completed right away since there are other orders before yours; this
resembles the receive queue. You hear the barista call out "vanilla latte for Jeff", but 
you're not Jeff so you wait. This idea of ignoring ties into the fact that all CAN nodes
are connect on the same Tx and Rx lines thus every message is received by all nodes.
Furthermore, our name acts as the Id for messages coming in/out. We wait and wait as 
more nodes get their order(data). Finally, the barista calls our name saying that our 
iced coffee is ready. We've got our iced coffee (data) and are ready to go finish our homework.