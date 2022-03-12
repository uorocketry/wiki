---
title: Interface Overhaul
description: 
published: true
date: 2022-03-12T17:58:46.492Z
tags: 
editor: markdown
dateCreated: 2022-03-12T17:58:46.492Z
---

# Problems
The current system has a few drawbacks:
- Inflexible to add specific IO configurations
  - E.g. adding support for supporting 1 or 2 temperature sensors is non-trivial
- A lot of preprecessor flags
  - Makes the code hard to understand
  - Possibly this is also slowing down compile times
- State sent to the Ground Station can change too easily, and requires changes to the Ground Station config
  - E.g. disabling the logger also removes that field being sent to the Ground Station
  - E.g. adding a new IO output is not compatible with a "old" Ground Station config