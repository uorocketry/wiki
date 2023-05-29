---
title: State Machine
description: The design docs for the state machine
published: true
date: 2023-05-29T04:18:40.553Z
tags: 
editor: markdown
dateCreated: 2023-05-29T04:15:50.984Z
---

# State Machine 
We are using the Rust SFSM crate https://docs.rs/sfsm/latest/sfsm/
## Logic Board
### States
- Wait for launch
- Ascent
- Descent 
- Landing 
- Wait for recovery 
- Abort 
### Transitions 
Initial state: Wait for launch 
Wait for launch -> Abort, Ascent 
Ascent -> Descent 
Descent -> Landing 
Landing -> Wait for recovery 
### Messages
- Vehicle status
	- Pressure 
  - Altitude 
  - Atitude 
  - Velocity  
## Recovery Board
### States
- Wait for drouge 
- Deploy drouge
- Wait for main
- Deploy main 
- Standby
### Transitions 
Wait for drouge -> Deploy drouge 
Deploy drouge -> Wait for main
Wait for main -> Deploy main
Deploy main -> Standby 
### Messages
- Ground station
	- Deploy drouge 
  - Deploy main 
  
## Power Board
### States
- Initalization 
- Ground power
- Onboard power 
### Transitions 
Initalization -> Ground power, Onboard power
Ground power -> Onboard power
Onboard power -> Ground Power 
### Messages 
- Status
	- Power source
  - Voltage
 	- Current