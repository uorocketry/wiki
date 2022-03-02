## Requirements
 - The Rocketry Laptop
 - Your personnal laptop

## Steps
1. Turn on the Rocketry Laptop and make sure it is connected to the eduroam network
2. Go on Settings -> Network -> Hotspot and turn on the hotspot. Do **not** change the name and the password
3. Connect your laptop to the hotspot
4. Turn on the Raspberry Pi and wait a little bit (it should automatically connect to the rocketry wifi hotspot)
5. You can now ssh into the raspberry pi and have internet access

#### for linux :
```
ssh pi@raspberrypi.local
```

## Additional notes
 - Some times, the hotspot turns off after 5 min of inactivity.
 - See the old tutorial if you want to connect the Raspberry Pi to a new network
 - For Sensor Suite, the static ip is 192.168.1.250 port 22 - Username=pi - password=david
 - For Fill Cart, the static ip is 192.168.1.150 port 22 - username=pi - password=raspberry 
 - the router gateway is 192.168.1.1
 - The router password is ipnhx30q07
 - The password for the router is admin