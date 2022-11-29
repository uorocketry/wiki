---
title: CAN Driver
description: 
published: true
date: 2022-11-29T03:42:38.764Z
tags: 
editor: markdown
dateCreated: 2022-11-29T03:42:38.764Z
---

# Overview
Steps of what needs to be done to activate and use CAN:

1. Setup the clocks
2. Init CAN
   1. Init registers
      1. Set CCR INIT + CCR CCE
      1. Configure various registers
         1. Set tx and rx fifo queue buffers
      1. Clear and enable CAN interrupts
      1. Clear CCR INIT + CCR CCE
      1. Wait until CCR INIT is set
   2. Setup callbacks
      1. Setups tx_done, rx_done, and irq_handler
3. Set GPIO pins


For interupts handler:
1. Check reason for interrupt call using IR register
2. Call appropriate callback

For sending a CAN message:
1. Register callback
   1. Set registers for callback "reason"
2. Enable CAN async
   1. Clear CCR Init bit
3. Call CAN write
   1. Create message
   2. Read buffer index/offset to write to
   3. Write to buffer
   4. Notify CAN about the new message to send
   
For receiving a CAN messsage:
1. Register callback
   1. Set registers for callback "reason"
2. On callback:
   3. Call CAN read
      1. Read message from buffer
      2. Notify that message has been read
      3. Note: It's possible to know the fill level of the buffer