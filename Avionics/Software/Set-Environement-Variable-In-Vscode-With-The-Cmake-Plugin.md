---
title: Set Environement Variable In Vscode With The Cmake Plugin
description: 
published: true
date: 2022-03-02T22:55:10.231Z
tags: 
editor: markdown
dateCreated: 2022-02-28T22:34:10.634Z
---

# Set up Cmake Kit In Vscode

First, open up your current kits using `Ctrl + shift + P` and "Edit User-Local Cmake Kits". Copy the data from the one you are currently using.

Create a file in the `.vscode` folder called `cmake-kits.json` and format it like below:

```
[{
    "name": "<name of kit>",
    "environmentVariables": {
        "<name of variable>": "1"
    },
    <DATA FROM EXISTING CMAKE KIT GOES HERE>
}]
```

Then, change your active kit and rebuild.

![Cmake Kit button](https://user-images.githubusercontent.com/12688112/87250980-76e1a980-c436-11ea-8d81-bc10759ebbec.png)

# Example Kit Config

```json
[{
    "name": "No Logs",
    "visualStudio": "6e824f2d",
    "visualStudioArchitecture": "x64",
    "preferredGenerator": {
      "name": "Visual Studio 15 2017",
      "platform": "x64",
      "toolset": "host=x64"
    },
    "environmentVariables": {
        "USE_LOGGER": "0"
    }
},
{
    "name": "Testing - No Logs",
    "visualStudio": "6e824f2d",
    "visualStudioArchitecture": "x64",
    "preferredGenerator": {
      "name": "Visual Studio 15 2017",
      "platform": "x64",
      "toolset": "host=x64"
    },
    "environmentVariables": {
        "TESTING": "1",
        "USE_LOGGER": "0"
    }
},
{
    "name": "Testing - With Logs",
    "visualStudio": "6e824f2d",
    "visualStudioArchitecture": "x64",
    "preferredGenerator": {
      "name": "Visual Studio 15 2017",
      "platform": "x64",
      "toolset": "host=x64"
    },
    "environmentVariables": {
        "TESTING": "1"
    }
}]
```
