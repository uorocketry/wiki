Linux:
* Download VSCode https://code.visualstudio.com/Download
* Open the terminal
* cd into the desired workspace
* `git clone https://github.com/uorocketry/rocket-code-2020.git --recurse-submodules`
* `cd rocket-code-2020`
* Setup the environment variables with this wiki page https://github.com/uorocketry/rocket-code-2020/wiki/Environment-Variables
* Install the necessary build tools using `sudo apt update && sudo apt install ninja-build cmake gcc make`. This command is for Debian/Ubuntu-based systems. It will vary between distros.
* Compile the project with - `./build.sh`
* Modify config.h file in the directory projects/HotFire folder to the following values: USE_RADIO, USE_GPIO, and USE_WIRING_PI to 0 and then type the command HOTFIRE_TEST=1 ./build.sh
* You can now run the project locally with - `./run.sh`


To update the github submodules
* `git submodule update --init --recursive`