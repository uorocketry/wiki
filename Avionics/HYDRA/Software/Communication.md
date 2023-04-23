---
title: Communication
description: 
published: true
date: 2023-04-23T20:09:16.976Z
tags: 
editor: markdown
dateCreated: 2023-04-23T19:30:26.889Z
---

# Communication
This document covers the communication of HYDRA 

## Requirments 
- Altitude and GPS 
	- f64 altitude above mean sea level in meters 
  - f64 latitude positive north
  - f64 longitude positive east
  - u32 timestamp since power up   
- Pitch, Yaw, Roll
  - [f32; 3usize] Roll, Pitch, Yaw angles 1 sigma standard deviation in rad
- Quaternions
	- [f32; 4usize] W, X, Y, Z form
  - u32 timestamp since power up 
- IMU 
	- [f32; 3usize] accelerometers X, Y, Z in m.s^-2
  - [f32; 3usize] gyroscopes X, Y, Z in rad.s^-1
  - f32 temperature in celcius
  - [f32; 3usize] delta velocity X, Y, Z in m.s^-2
  - [f32; 3usize] delta angle X, Y, Z in rad.s^-1
- States 
	- Probably a [u8], TBD on the state machine implementation 
- Power status
	- TBD
- Radio status 
	- TBD dependant on the data that the RFD 900 injects 
## Rocket to Ground
Using an RFD 900 to transmit data on 902MHz.
Current packet system is COBS, to be changed to MAVLINK.

## Ground to Rocket
To be implemented in later versions 