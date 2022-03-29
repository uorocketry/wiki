---
title: Usage
description: 
published: true
date: 2022-03-29T16:46:19.872Z
tags: 
editor: markdown
dateCreated: 2022-03-29T16:45:07.781Z
---

Connect to via ssh to the sensor suite raspberry pi (See [here](/en/Avionics/Software/Connect-to-Raspberry-Pi-via-SSH) for the ip)

## Normal Usage

Logs to file to until Ctrl c in data-unixtimestamp. Prints data every second

```bash
cd Cistern/code
python3 Main.py
```

## Testing if everything is connected
Prints data from pressure sensor and other sensors **once** to the screen for testing purposes

```bash
cd Cistern/code
python3 Display.py
```