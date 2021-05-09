Linux:
* Download VSCode https://code.visualstudio.com/Download
* Open the terminal
* cd into the desired workspace
* `git clone https://github.com/uorocketry/rocket-code-2020.git --recurse-submodules`
* `cd rocket-code-2020`
* Setup the environment variables with this wiki page https://github.com/uorocketry/rocket-code-2020/wiki/Environment-Variables
* Install the necessary libraries and build tools: `ninja-build`, `cmake`, `gcc`, `make`, `boost with filesystem`
  * Command for Debian/Ubuntu: `sudo apt && sudo apt install ninja-build cmake gcc make libboost-all-dev`. Replace `libboost-all-dev` with `libboost-filesystem-dev` if you don't want to install the entire boost library.
* Compile the project with - `./build.sh`
    * To run the Hotfire test code without a pi - `USE_RADIO=0 USE_GPIO=0 USE_WIRING_PI=0 HOTFIRE_TEST=1 ./build.sh`
* You can now run the project locally with - `./run.sh`

To update the github submodules
* `git submodule update --init --recursive`