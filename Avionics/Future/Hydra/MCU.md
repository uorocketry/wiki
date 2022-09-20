---
title: MCU
description: 
published: true
date: 2022-09-20T02:21:03.186Z
tags: 
editor: markdown
dateCreated: 2022-09-19T21:23:02.880Z
---

# Options
## STM32G431KB
- Cortex-M4 MCU 170 MHz, 128K Flash, 32K RAM
- Single FDCAN Controller
- 12 bit ADCs
- 32 pins, LQFP
- https://www.newark.com/stmicroelectronics/stm32g431kbt6/mcu-32bit-170mhz-lqfp-32/dp/17AH9352?st=stm32g431k
- Dedicated motor controller support
- Has dev boards

## ATSAME54N19A
- No longer in stock

## ATSAME51J18A
- Cortex-M4 MCU 120 MHz, 256K Flash, 128K RAM
- 2 FDCAN Controllers
- SDHC Controller
- 12 bit ADCs
- 64 pins, VQFN
- Has dev boards

# Decision
Overall, both chips are similar. However, for the main chip, the ATSAME51J18A is ideal with its two CANFD controllers and the extra flash/RAM. It also has more pins and extra memory, allowing the chip to do more functions if needed.

Regarding support, the STM32 chips seems to be more widely used, which means there is more information online on how to use those chips. However, at first look, the documentation and software for the SAM chips seems to be more user-friendly and more accessible.

Therefore, we decided to go with the ATSAME51J18A. It's the obvious choice for the main chip with its two CANFD controllers and extra memory. For the nodes, both MCUs could be used, so to keep the overall system simpler, we'll go again with the same chip. Both chips have around the same price, but the ATSAME51J18A has slightly better specs.