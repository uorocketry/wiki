---
title: Radio commands in Python 3
description: 
published: true
date: 2022-03-02T22:54:03.106Z
tags: 
editor: markdown
dateCreated: 2022-02-28T22:33:51.147Z
---

### To setup the radio communication on the groundstation

```
import Serial
ser = serial.Serial("COM3", 57600, timeout=1)
```

### To enter AT command mode on the radio

```
ser.write(b"+++")
```

### To Enable RSSI Debugging infos

```
ser.write(b"AT&T=RSSI\r\n")
```

### To Exit AT command mode

```
ser.write(b"ATO\r\n")
```

Then, the radio should send debug messages containing the RSSI and noise infos looking like this
```
L/R RSSI: 218/218  L/R noise: 73/70 pkts: 4  txe=0 rxe=0 stx=0 srx=0 ecc=0/0 temp=22 dco=0\r\n
```

Those message will never be in the middle of a packet, nor the packet will be in the middle of this message. 