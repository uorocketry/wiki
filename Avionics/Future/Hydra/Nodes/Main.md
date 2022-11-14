---
title: Main Node
description: 
published: true
date: 2022-11-14T20:08:51.960Z
tags: 
editor: markdown
dateCreated: 2022-10-22T02:04:37.439Z
---

# Base Software Changes
Please keep note of any changes to the HAL, HPL, or HRI of the ASF4 as well as the SBGECom.
## ASF4
- Created a non-static (so we can access out side of the file) method for convert date_time structure to UNIX timestamp as needed by the SBG. -> Probaly could just remove the static declaration for the base function this calls. 
- Changed the read timeout of the RTOS UART to 1... I believe that this is one RTOS tick so 1ms. Should be changed to a higher value like 10ms.
## SBG
- Provided a platform specific implementation of sleep and get time.
- Changed all declarations of assert to the utils_assert ASSERT implementation. I choose not to define assert in the SBG defines file since it conflicted with the utils_assert assert and microchip whishes you use ASSERT. 