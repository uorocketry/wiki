---
title: Main Node
description: 
published: true
date: 2022-11-10T21:30:12.917Z
tags: 
editor: markdown
dateCreated: 2022-10-22T02:04:37.439Z
---

# Base Software Changes
Please keep note of any changes to the HAL, HPL, or HRI of the ASF4 as well as the SBGECom.
## ASF4

## SBG
- Provided a platform specific implementation of sleep and get time.
- Changed all declarations of assert to the utils_assert ASSERT implementation. I choose not to define assert in the SBG defines file since it conflicted with the utils_assert assert and microchip whishes you use ASSERT. 