---
title: Environment Variables
description: 
published: true
date: 2022-03-02T22:51:15.075Z
tags: 
editor: markdown
dateCreated: 2022-02-28T22:32:58.588Z
---

#### Projects
Default is October Sky

`HOTFIRE_TEST`: Run HotFire test.


#### For Development

`SKIP_INIT`: Don't wait for sensors to initialize before switching to the first state.

`TESTING`: Enable sensor testing and load sensor data from a testing file instead of real sensors. [See here](./Testing-With-Predefined-Sensor-Data)

`USE_LOGGER`: Enable logging to a file. [See here](./Disable-Logging-To-A-File)

`TARGET_UPDATE_DURATION_NS`: Target duration for each logic update. Default: `33333333` (30 Hz)

##### File Paths

`LOG_PATH`: Path where log files should be saved. Default: `"/data/"`

`TESTING_INPUT_FILE`: File that contains sensor data for testing, only used if `TESTING` is enabled. Default: `"./data/test-data.csv"`

#### Sensors

`USE_SBG`: Enable SBG Sensor

`USE_INPUT`: Enable stdin listener that can control the states

# Setup

On Linux/WSL:

**Set**: `export <variable-Name>=1`

**Unset**: `unset <variable-Name>`

You can also [set this up with Vscode](./Set-Environement-Variable-In-Vscode-With-The-Cmake-Plugin)
