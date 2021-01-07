#### Projects
Default is October Sky

`HOTFIRE_TEST`: Run HotFire test.


#### For Development

`SKIP_INIT`: Don't wait for sensors to initialize before switching to the first state.

`TESTING`: Enable sensor testing and load sensor data from a testing file instead of real sensors. [See here](https://github.com/uorocketry/rocket-code-2020/wiki/Testing-With-Predefined-Sensor-Data)

`USE_LOGGER`: Enable logging to a file. [See here](https://github.com/uorocketry/rocket-code-2020/wiki/Disable-Logging-To-A-File)

### File Paths

`LOG_PATH`: Path where log files should be saved. Default: `"/data/"`

`TESTING_INPUT_FILE`: File that contains sensor data for testing, only used if `TESTING` is enabled. Default: `"./data/test-data.csv"`

#### Sensors

`USE_SBG`: Enable SBG Sensor

`USE_SOCKET_CLIENT`: Enable TCP server that can control the states remotely

`USE_INPUT`: Enable stdin listener that can control the states


# Setup

On Linux/WSL:

**Set**: `export <variable-Name>=1`

**Unset**: `unset <variable-Name>`

You can also [set this up with Vscode](Set-Environement-Variable-In-Vscode-With-The-Cmake-Plugin)
