---
title: Rocket to Ground Station Proxy
description: 
published: false
date: 2022-11-21T01:53:40.914Z
tags: 
editor: markdown
dateCreated: 2022-11-21T01:50:30.043Z
---

## MavLink Understanding
- Mavlink will do the checksum checks for us 

- The cheksum ensure that the data has not been altered and it also ensures that the two messages with the same ID are containing the same information. The refrence implementations store this constant in an array called CRC_EXTRA after it is run through CRC-16-CCITT and the resulting value is used to seed the packet CRC

- At the start of a mavlink message there is a byte that indicates the start of a new packet

---

This image details how is a mavlink message formatted 

![mavlink-frame.png](/mavlink-frame.png)

---

