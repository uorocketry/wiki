---
title: Sensor Suite Testing (2022-09-28)
description: 
published: true
date: 2022-09-28T20:53:04.482Z
tags: 
editor: markdown
dateCreated: 2022-09-28T20:53:04.482Z
---

Sensor suite testing:

* tested with AC, lights look the correct brightness and no voltage errors in kernel logs
* tested with power supply + inverter, lights look the correct brightness and no voltage errors in kernel logs
* attempted to test with power supply 5v directly to see if I can reproduce the voltage errors in kernel logs, but for some reason it won't power with it anymore? AC still works so I didn't fry it (I can see the old ones from the boot logs, so I do know for sure they did exist at some point)