---
title: Overview
description: 
published: true
date: 2023-06-07T00:15:54.962Z
tags: 
editor: markdown
dateCreated: 2023-06-07T00:07:02.964Z
---

# Boards Purpose

Power Board:
- Send current, voltage, along with its current power source
- Communicate its status (Ok, Failure)

Sensor Board:
- Read from SBG and dumps to CAN bus, along with SD Card
- Monitor CAN Bus and write all messages to SD Card
- Control Buzzer

Communication Board:
- Receive data from CAN Bus and send to radio
- Receive data from radio and send to CAN Bus
- Implement rate limiting on sensor information (ONLY sensor information)
- Monitor radio status and rate limit on logs and sensor if buffer is starting to fill up

> How exactly should the communication about the rate limiting happen between the recovery board and the communication board?

Recovery Board:
- Sends and stores information about its backup IMU and baro
- Stores sensor information from the sensor board
- Runs a state machine that transitions based on:
	 - Sensor information
   - Ground station commands (e.g. arming)
- Control drogue and parachute based on state machine
- Send board and state machine status