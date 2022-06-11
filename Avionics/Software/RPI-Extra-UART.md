---
title: Extra UARTs on the Raspberry Pi
description: 
published: true
date: 2022-06-11T17:12:34.310Z
tags: 
editor: markdown
dateCreated: 2022-06-11T17:12:34.310Z
---

# Raspbery Pi UARTs
By default, the RPi has 1 UART enabled for GPIO (there is another for Bluetooth, but let's ignore that one for now). However, it's possible to enable up to 6 UARTs.

To enable a UART just add this line to the end of the `/boot/config.txt` file:
```
dtoverlay=uart2
```

This will enable UART2, which can be accessed at `/dev/ttyAMA1` after a reboot. TX is on GPIO 0, and RX is on GPIO 1.

`uart2` to `uart6` are also available. Please see the `/boot/overlays/README` for more information, for example which pins each UART uses.

See the Raspberry Pi documentation for more information: https://www.raspberrypi.com/documentation/computers/configuration.html#raspberry-pi-4-and-400.