---
title: Hardware Requirements
description: 
published: true
date: 2022-09-14T02:29:20.763Z
tags: 
editor: markdown
dateCreated: 2022-09-14T02:13:51.619Z
---


# Board Specific Requirements
## General
All chips must:
- Have a green power LED. Must be on whenever there is power.
- Have a blue communication LED. Connected to a digital out pin on the MCU.
- Have a red error LED. Connected to a digital out pin on the MCU.
- Expose SWD debug connection to the chip.
  - Must have standard connector. Need to research what is the name of this connection. See https://www.st.com/en/development-tools/stlink-v3set.html or https://www.segger.com/products/debug-probes/j-link/models/j-link-edu-mini/ for the debugger that we'll use.
- Use the STM32G431KBT6 MCU.
- Communicate to other chips using FDCAN.

## State Machine Board
No special requirements

## Data Logging Board
- Interface with SD Card (probably SPI? TODO find specific card)

## Communication Board
- TODO: Need to research on Ethernet or RS-485?

## Temperature Board
- Interface with up to 4 MAX31855 amplifier boards (https://www.adafruit.com/product/269)
  - All boards are connected to the same SPI bus
  
## Pressure Transducer Board
- TODO: Do we only need to have those connect to the ADC? Could we have generic ADC boards?

## Load Cell Board
- TODO


# Resources
ADC Tips: https://www.st.com/resource/en/application_note/an5346-stm32g4-adc-use-tips-and-recommendations-stmicroelectronics.pdf
ADC Accuracy: https://www.st.com/resource/en/application_note/an2834-how-to-get-the-best-adc-accuracy-in-stm32-microcontrollers-stmicroelectronics.pdf
ESD Protection: https://www.st.com/resource/en/application_note/an5612-esd-protection-of-stm32-mcus-and-mpus-stmicroelectronics.pdf