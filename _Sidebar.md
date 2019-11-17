# Emulating Raspberry Pi using QEMU on Ubuntu
In order to use the emulator, you must install QEMU emulator that emulates ARM on your computer.
`sudo apt-get install qemu-kvm qemu virt-manager virt-viewer libvirt-bin` When you are done,
you'll need a Raspberry Pi kernel and a disk image that has contents of SD card on the physical Raspberry Pi.

Once you have everything, make a bash file called `config` and write into the following:
`#!/bin/bash`
`# Starts raspberry pi image in configuration mode`
 
`qemu-system-arm -kernel ./qemu-rpi-kernel/kernel-qemu-4.4.34-jessie -cpu arm1176 -m 256 -M versatilepb -no-reboot``-serial stdio -append "root=/dev/sda2 panic=1 rootfstype=ext4 rw init=/bin/bash" -hda /dev/mmcblk0`

You can change the last part -hda /dev/mmcblk0 to any location you want. Please know the location of your SD Card!

When you want to run the emulation: type `sudo ./config`

That's it. You get the emulation

 