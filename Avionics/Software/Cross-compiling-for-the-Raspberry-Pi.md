You can cross compile the project for a raspberry pi on a Linux system.

Make sure you have all the dependencies installed as outlined in the [Getting started page](Getting-started).

### Downloading raspberry pi tools

To cross compile you will need a local copy of the raspberry pi tools repository. Run the following command:

```bash
git clone --depth 1 https://github.com/raspberrypi/tools.git
```

The cloned repository will be around 1gb so the command will take some time to finish.

### Cross compiling boost

Once you've cloned the raspberry pi tools, you will now need to compile [boost's filesystem library](https://www.boost.org/doc/libs/1_75_0/libs/filesystem/doc/index.htm) for arm.

There is a helper script, `/build-boost-arm.sh` that will automate this process. The script will download boost to a `boost_1_70_0` directory and compile it for arm in that same directory. To use it you will need to set the `RPI_TOOLS` environment variable to the path of the raspberry pi tools repository you cloned above.

Example of running the script:

```bash
# cd out of the repository
cd ..

# set the RPI_TOOLS environment variable
export RPI_TOOLS=/path/to/raspberry/pi/tools

# run the script, it will create a boost_1_70_0 directory
./feat-cross-compilation/build-boost-arm.sh
```

### Cross compiling libi2c
To cross compile you will need to set two environment variables:

- `RPI_TOOLS` which points to the path of the raspberry pi tools repository you cloned above

Run `build-libi2c.sh`

The libi2c library should be install in the `i2c-tools-4.3/` folder

### Cross compiling 

To cross compile you will need to set two environment variables:

- `RPI_TOOLS` which points to the path of the raspberry pi tools repository you cloned above
- `BOOST_DIRECTORY` which points to the cross compiled boost directory you created above
- `LIBI2C_DIRECTORY` which points to the cross compiled libi2c directory you created above

Finally, run the `/build-arm.sh` script:

```bash
# set the required environment variables
export RPI_TOOLS=/path/to/raspberry/pi/tools
export BOOST_DIRECTORY=/path/to/boost_1_70_0
export LIBI2C_DIRECTORY=/path/to/libi2c


# build the project
./build-arm.sh
```

Your final arm executable will be at `/build-arm/MainLoop`.

If you don't want to set the environment variables above every time you can append the following to your `.bashrc` file:

```bash
export RPI_TOOLS=/path/to/raspberry/pi/tools
export BOOST_DIRECTORY=/path/to/boost_1_70_0
export LIBI2C_DIRECTORY=/path/to/libi2c

```
