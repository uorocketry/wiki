---
title: Testing With Predefined Sensor Data
description: 
published: true
date: 2022-03-02T22:55:54.736Z
tags: 
editor: markdown
dateCreated: 2022-02-28T22:34:24.009Z
---

To enable testing mode, define the `TESTING` environment variable.

On Linux/WSL:

**Set**: `export TESTING=1`

**Unset**: `unset TESTING`

You can also [set this up with Vscode](Set-Environement-Variable-In-Vscode-With-The-Cmake-Plugin)

### Testing Data

Testing data is a csv formatted in the same way as the log files (located at `LOG_PATH`, default `/data/`). Unlike the log files, it should have all data in one file.

This file should be placed in the location specified by `TESTING_INPUT_FILE` (default `./data/test-data.csv`).