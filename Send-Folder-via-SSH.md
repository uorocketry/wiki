We recommend to send only the `build-arm` folder because it is smaller

`cd build-arm`

Then, you can send the folder to the raspberry pi with this command

`rsync -r . pi@ip_address:/home/pi/cross-compilation`
