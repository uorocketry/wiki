---
title: Thermo couple
description: 
published: true
date: 2022-11-28T01:01:42.574Z
tags: 
editor: markdown
dateCreated: 2022-11-28T00:22:02.800Z
---

# Thermocouple ADC conversion
## 1. [Polynomial  Equation](http://www.mosaic-industries.com/embedded-systems/microcontroller-projects/temperature-measurement/thermocouple/type-k-calibration-table)

$\frac{\left(x-V_{0}\right)\cdot\left(P_{1}+\left(x-V_{0}\right)\cdot\left(P_{2}+\left(x-V_{0}\right)\left(P_{3}+p_{4}\left(x-V_{0}\right)\right)\right)\right)}{1+\left(\left(x-V_{0}\right)\cdot\left(Q_{1}+\left(x-V_{0}\right)\cdot\left(Q_{2}+Q_{3}\cdot\left(x-V_{0}\right)\right)\right)\right)}$

## Implementation
The following implementation uses values for temperature ranges `-100 to 100°C`. The limitation to the polynomial method is that it is an estimation of certain intervals of values of voltage. For temperatures outside this range, the function will have  a higher margin of error.
```c++
float calcTemp(float v)
{
    float T0 = -8.7935962;

    float V0 = -3.4489914e-1;

    float P1 = 2.5678719e1;
    float P2 = -4.9887904e-1;
    float P3 = -4.4705222e-1;
    float P4 = -4.4869203e-2;

    float Q1 = 2.3893439e-4;
    float Q2 = -2.0397750e-2;
    float Q3 = -1.8424107e-3;
    
    float p = (v - V0) * (P1 + (v - V0) * (P2 + (v - V0) * (P3 + P4 * (v - V0))));
    float q = 1 + ((v - V0) * (Q1 + (v - V0) * (Q2 + Q3 * (v - V0))));
    
    float temp = T0 + p / q;
    return temp;
}
```

## 2. [Look-up table](https://srdata.nist.gov/its90/download/type_k.tab)

