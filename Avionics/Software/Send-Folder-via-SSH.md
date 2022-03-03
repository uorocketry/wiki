---
title: Send Folder via SSH
description: 
published: true
date: 2022-03-02T22:54:43.453Z
tags: 
editor: markdown
dateCreated: 2022-02-28T22:34:03.843Z
---

We recommend to send only the `build-arm` folder because it is smaller

`cd build-arm`

Then, you can send the folder to the raspberry pi with this command

`rsync -r . pi@ip_address:/home/pi/cross-compilation`
