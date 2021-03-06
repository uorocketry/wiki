---
title: Getting Started with the Rocket-Code
description: 
published: true
date: 2022-03-24T14:50:24.461Z
tags: 
editor: markdown
dateCreated: 2022-02-28T22:33:05.275Z
---

* If using Windows, install WSL: https://docs.microsoft.com/en-us/windows/wsl/install-win10#manual-installation-steps
  * Both WSL 1 or WSL 2 should work. However, when in doubt, WSL 2 is probably a better choice.
* Download VSCode https://code.visualstudio.com/Download
* Open the terminal (if on Windows, use a WSL terminal)
* cd into the desired workspace
* `git clone https://github.com/uorocketry/rocket-code-2020.git --recurse-submodules`
* `cd rocket-code-2020`
* Install the necessary libraries and build tools: `sudo ./install-dependencies.sh`
* Compile the project with `./build.sh`
    * To run the Hotfire test code without a pi - `USE_LOGGER=0 USE_GPIO=0 HOTFIRE_TEST=1 ./build.sh`
* You can now run the project locally with - `./run.sh`

If on Windows, see [Developing on Windows with VSCode](./Developing-on-Windows-with-VSCode)

To update the github submodules
* `git submodule update --init --recursive`

Once you are setup:
- Try running the unit tests by running `./unitTest.sh` and make sure it all passes. Run the end-to-end test with `cd ./tests/octoberSky/; bash ./run_test.sh "Unix Makefiles"`

- Check the stuff in the [Next Up column](https://github.com/uorocketry/rocket-code-2020/projects/1#column-14620035) in the GitHub project
- Check out how to set up the environment variables with this wiki page https://github.com/uorocketry/rocket-code-2020/wiki/Environment-Variables