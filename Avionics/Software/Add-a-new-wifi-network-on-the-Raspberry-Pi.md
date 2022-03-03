---
title: Add a new wifi network on the Raspberry-Pi
description: 
published: true
date: 2022-03-02T22:44:59.690Z
tags: 
editor: markdown
dateCreated: 2022-02-28T22:32:06.953Z
---

This is if you want to add a new wifi network on the Raspberry Pi

## Requirements
 - Laptop with Windows (for the hotspot)
 - Laptop with a Linux distro and a SD card reader

## Steps
1. Set up a wifi hotspot on the Windows laptop
2. With the Linux laptop, open the wpa-supplicant configuration file on the SD card. This file is located on the partition that contain all the files (not the boot partition). You will need a linux laptop because it is a linux partition (don't work with windows or mac).

```
sudo nano path-to-sd-card/etc/wpa_supplicant/wpa_supplicant.conf
```

3. Go to the bottom of the file and add the following (or modify the previous one): 
```
network={
    ssid="name-of-the-hotspot"
    psk="password-of-the-hotspot"
}
```

4. Once done, save the file, eject the SD card, put it into the raspberry pi and boot it. It should automatically connect to the hotspot.

5. Connect your personnal laptop (or other devices) to the hotspot
6. You can now ssh into the raspberry pi and have internet access

#### for linux :
```
ssh pi@raspberrypi.local
```


