---
title: Ground Station
description: Design notes of the ground station 2022/2023
published: true
date: 2023-01-26T01:02:33.015Z
tags: 
editor: markdown
dateCreated: 2023-01-26T01:00:52.853Z
---

# Ground Station
Diagram: 
![ground_station.drawio.png](/ground_station.drawio.png)

## RGS
- Receive JSON from proxy 
- Change socket.io to ZeroMQ 
- Add support for specific sensors (after ZeroMQ is configured)  
## Java Ground Station
- Receive JSON from proxy  
## Proxy
- Create ZeroMQ instance  
- Allow Mock Rocket data in JSON format for testing  
## Rocket
- MavLink (To be completed after postcard is supported by the proxy) 