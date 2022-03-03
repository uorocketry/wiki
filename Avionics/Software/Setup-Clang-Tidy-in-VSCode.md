---
title: Setup Clang Tidy in VSCode
description: 
published: true
date: 2022-03-02T22:55:36.759Z
tags: 
editor: markdown
dateCreated: 2022-02-28T22:34:17.405Z
---

1. Install `clang-tidy` in your environment (`sudo apt update && sudo apt install clang-tidy`)
2. Install the [Clang-Tidy](https://marketplace.visualstudio.com/items?itemName=notskm.clang-tidy) extension
3. Add the following lines to `.vscode/settings.json`

```json
"clang-tidy.checks": [
    "clang-diagnostic-*",
    "clang-analyzer-*",
    "-*",
    "bugprone*",
    "modernize*",
    "performance*",
    "-modernize-use-trailing-return-type"
],
"clang-tidy.buildPath": "./build"
```