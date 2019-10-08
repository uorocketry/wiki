## RequirementS
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

## Additional notes
Later on, we will use a specific laptop for the hotspot. The settings will be already configured, so you won't have to modify the SD card.

