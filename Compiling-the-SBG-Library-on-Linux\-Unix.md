Run `./build-and-run.sh` to build and run automatically.

# Manually

Here's how to compile the SBG example code on your laptop with the SBG connected via USB.

1. go to: `cd <path_where_SBG_folder_is>/SBG/Software\ Development/sbgECom/projects/unix`
2. run `cmake -G 'Unix Makefiles'` to generate makefiles for the example `.c` file
3. run `make` to actually compile 
4. go to: `cd <path_where_SBG_folder_is>/SBG/Software\ Development/sbgECom/bin`
5. run the example with: `./ellipseMinimal`

The actual source code is in: `cd <path_where_SBG_folder_is>/SBG/Software\ Development/sbgECom/examples/ellipseMinimal/src`

The firmware guide should be in `<path_where_SBG_folder_is>/SBG/Documentation/Common`


Things you might have to do:
- determine which serial port the SBG is on (usually when you list your serial ports you'll see a description like `FTDI device` or something involving FTDI
  - after you know what it is, modify the `.c` file to match that port, it should be something like: 
```c
	errorCode = sbgInterfaceSerialCreate(&sbgInterface, "/dev/TTYUSB0", 921600);		// Example for Unix using a FTDI Usb2Uart converter
```

you should change the `"/dev/TTYUSB0"` to match your serial port