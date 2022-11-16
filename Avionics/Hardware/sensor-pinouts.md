---
title: Sensor Pinouts
description: cable and connector pin assignments for pressure transducers, load cells, etc.
published: true
date: 2022-11-16T22:09:39.919Z
tags: 
editor: markdown
dateCreated: 2022-10-25T19:13:48.365Z
---



**Button Load Cell Loadstar Sensors**
1000kg

| Connector Pin | Wire Color | Assignmnet   |
|---------------|------------|--------------|
| 1             | RED        | Excitation + |
| 2             | GREEN      | Signal +     |
| 3             | BLACK      | Excitation - |
| 4             | WHITE      | Signal -     |
| 5             | SHIELD     | Shield       |


**Pressure Transducer MEAS M3031-000005-2K5PG**
0.5-4.5V, 0-2500psi

| Connector Pin | Wire Color | Assignmnet   |
|---------------|------------|--------------|
| 1             | RED        | +5V          |
| -             | GREEN      | N/C          |
| 2             | BLACK      | GND          |
| 3             | WHITE      | Signal Out   |
| 4             | SHIELD     | Shield       |


**12V Power**

| Connector Pin | Wire Color | Assignmnet   |
|---------------|------------|--------------|
| 1             | BLACK      | GND          |
| 2             | RED        | +12V         |

**GX Series Circular Connectors**
- Connect pins according to the sensor pinouts
- Strip only enough insulation from the individual wires to expose the soldered areas - snip the wires after tinning then if they're to long
- Tin the wires first (to make soldering easier)
- Ensure cable insulation extends slightly past the clamp on the connector
- Make sure not to damage the wires (especially shield drain wire) when stripping the cable. Re-cut and strip cable ends if damaged
- Use a single piece of heat shrink to cover all the terminals (less than 1/3 of a tube is required)

![gx-connect-solder-2.png](/gx-connect-solder-2.png)
![gx-connect-solder-1.png](/gx-connect-solder-1.png)

