---
title: Rocket to Ground Station Proxy
description: 
published: false
date: 2022-11-21T02:27:24.639Z
tags: 
editor: markdown
dateCreated: 2022-11-21T01:50:30.043Z
---

## MavLink Understanding
- Mavlink has checksums we can use theri APIs to do the message checks
- The cheksum ensure that the data has not been altered and it also ensures that the two messages with the same ID are containing the same information. The refrence implementations store this constant in an array called CRC_EXTRA after it is run through CRC-16-CCITT and the resulting value is used to seed the packet CRC
- At the start of a mavlink message there is a byte that indicates the start of a new packet
- MavLink messages can't be more than 263 bytes
>  - -The sender always fills in the ```System ID``` and ```Component ID``` fields so that the receiver knows where the packet came from. The ```System ID``` is a unique ID for each vehicle or ground station. Ground stations normally use a high system id like “255” and vehicles default to use “1” (this can be changed by setting the SYSID_THISMAV parameter). The ```Component ID``` for the ground station or flight controller is normally “1”. Other MAVLink capable device on the vehicle (i.e. companion computer, gimbal) should use the same System ID as the flight controller but use a different Component ID 
		-The ```Message ID``` field can be seen in the common.xml and ardupilot.xml next to the message name. For example the HEARTBEAT message Id is “0”
    -Source:https://ardupilot.org/dev/docs/mavlink-basics.html
{.is-info}

---

This image details how is a mavlink message formatted 

![mavlink-frame.png](/mavlink-frame.png)

---

> Are we going to use custom dialects for the rocket?


