---
title: Usage
description: 
published: true
date: 2022-03-29T16:36:21.100Z
tags: 
editor: markdown
dateCreated: 2022-03-29T16:36:21.100Z
---

For Hotfire test, download the latest build at https://nightly.link/uorocketry/rocket-ground-station/workflows/build/master/GroundStationWithHotfireConfig.zip.zip

Extract this, and run `GroundStation.jar`. If it doesn't run by double clicking, you can run it from the command line with `java -jar GroundStation.jar`

## Connect to rocket code

Select the connection type (Serial for radio, TCP for ethernet) and click connect.

The rocket code will be at ip `192.168.1.150` port `8080`.

![gs-connection.png](/gs-connection.png)

## Controlling rocket code

![ground-station-control.png](/ground-station-control.png)

Control the states with the buttons on the right.

Buttons are blue when they can be pushed, green when their states have been passed and grey when they don't trigger anything to happen.

Change the chart by clicking on columns in the table on the left. Right clicking on columns sets that column as the X value.