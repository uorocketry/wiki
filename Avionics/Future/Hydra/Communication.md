---
title: Communication
description: 
published: false
date: 2022-10-18T23:51:41.612Z
tags: 
editor: markdown
dateCreated: 2022-10-18T23:51:41.612Z
---

# Overview
Hydra nodes communicate over CAN FD. Any messages are broadcasted over to all nodes in the CAN network, requiring filtering to be done on each node. 

CAN FD is pretty low-level, similar to Ethernet. For any useful communication to happen, some form of protocol must be agreed upon and used by all nodes. CAN FD allows a payload of up to 64 bytes. For Hydra, these are the rough goals of this protocol:
- Allocate unique IDs to each node
- Send sensor data
- Send node status/health
- Send reliable commands between nodes

# ID Allocation
CAN FD allows the choice of an 11-bit identifier or an 29-bit identifier. This identifier must be unique through the CAN network, else collisions can happen.

The ID also doubles as the message priority, with a lower ID representing a higher priority. If two nodes try to send at the same time, the one with the highest ID will back off and allow the other node to send its message.

# Serialization Format