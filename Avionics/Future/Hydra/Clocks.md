---
title: Clocks and Crystals
description: 
published: true
date: 2022-11-07T21:46:26.168Z
tags: 
editor: markdown
dateCreated: 2022-11-07T21:36:39.388Z
---

# Clocks and Crystals
These crystals won't help your chakra haha. 
## 32.768 KHz 
- We want a stable reference for our RTOS and input into the DFLL.
- Most common frequency for RTOS due to the ability to divide down to 1Hz. 
- DFLL may only take 32.768KHz.
## 16 MHz 
- 16MHz/5 = 3.2MHz the max value we can pass to our DPLL. 
## DFLL 
Always going to be 48MHz for the ATSAME51J20A
## DPLL 
Reference range of 32KHz to 3.2MHz. 
Output range 96 MHz to 200 MHz.
### Calculation 
LDRFRAC -> Loop divider ratio fractional part
LDR -> Loop divider ratio integer part
Fckr -> reference clock 
Fclk_dpll=Fckr*(LDR+1+LDRFRAC/32)