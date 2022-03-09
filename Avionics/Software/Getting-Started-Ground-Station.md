---
title: Getting Started with the Ground Station
description: 
published: true
date: 2022-03-09T02:16:33.904Z
tags: 
editor: markdown
dateCreated: 2022-03-09T02:16:33.904Z
---

It's recommended to use IntelliJ Idea to do development (https://www.jetbrains.com/idea/). These instructions will assume this IDE is used.

1. Clone the repo: https://github.com/uorocketry/rocket-ground-station
2. Open the project in [IntelliJ as a Gradle project](https://www.jetbrains.com/help/idea/gradle.html#gradle_import_project_start)
3. Copy `data/config-hotfireTest.json` to `data/config.json`
3. Run the project (Shift+F10 or the run button top right)
4. To connect to a rocket-code instance running locally, change the `Rocket` connection type to `TCP`, and click `Connect`
5. It's possible there are some parsing errors in the logs due to a mismatch of the config between the rocket-code and the ground-station. Please ask in the Avionics Slack channel for the latest version.