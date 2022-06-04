---
title: Mavlink
description: 
published: true
date: 2022-06-04T22:08:03.215Z
tags: 
editor: markdown
dateCreated: 2022-06-04T21:52:02.593Z
---

### Read mavlink data over serial with python


> Note: To access `/dev/ttyUSB` on Linux without root, you may need to add your user to a user group
> ```bash
> sudo usermod -a -G uucp <your-username-goes-here>
> ```

Script to read data:

Run it with `python -i file.py`, then run `get()`

```python
from pymavlink import mavutil

# You may need to increment this (ex. /dev/ttyUSB1), will be different on Windows
the_connection = mavutil.mavlink_connection("/dev/ttyUSB", baud=57600, source_system=1)

def send_heartbeat():
    the_connection.mav.heartbeat_send(0, 0, 0, 0, 0)
    print("heartbeat sent")


def get():
    send_heartbeat()
    return the_connection.recv_match(blocking=True)
```
  
The result is

```
heartbeat sent
RADIO {rssi : 63, remrssi : 0, txbuf : 100, noise : 58, remnoise : 0, rxerrors : 0, fixed : 0}
heartbeat sent
RADIO_STATUS {rssi : 63, remrssi : 0, txbuf : 100, noise : 58, remnoise : 0, rxerrors : 0, fixed : 0}
```