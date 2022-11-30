---
title: Thermo couple
description: 
published: true
date: 2022-11-30T05:32:57.608Z
tags: 
editor: markdown
dateCreated: 2022-11-28T00:22:02.800Z
---

# Thermocouple ADC conversion
## 1. [Polynomial  Equation](http://www.mosaic-industries.com/embedded-systems/microcontroller-projects/temperature-measurement/thermocouple/type-k-calibration-table)

$T_{0}+\frac{\left(x-V_{0}\right)\cdot\left(P_{1}+\left(x-V_{0}\right)\cdot\left(P_{2}+\left(x-V_{0}\right)\left(P_{3}+p_{4}\left(x-V_{0}\right)\right)\right)\right)}{1+\left(\left(x-V_{0}\right)\cdot\left(Q_{1}+\left(x-V_{0}\right)\cdot\left(Q_{2}+Q_{3}\cdot\left(x-V_{0}\right)\right)\right)\right)}$

## Implementation

The following implementation uses constants for temperature ranges `-100 to 100°C`. The limitation to the polynomial method is that it is an estimation of values of voltage between a specific interval. For temperatures outside this range, the function will have  a higher margin of error. For example, the constants used in the example would give a wrong value for temperatures above `100°C`. The ranges provided in the datasheet are only `200°C` apart.

```c++
/**
 * @param {float} v - voltage in microvolts
 * @returns {float} temperature in °C
*/
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

First, import the lookup table as an array into your program. Use the following data:

- [Copy C++ lookup table(curly bracket)](https://uottawa.sharepoint.com/teams/uORocketry/_layouts/15/guestaccess.aspx?guestaccesstoken=PRyVBsH%2B%2FrF7grl9ZETexMRx9crHjMSTFri%2BdDSZnAY%3D&docid=2_05c6badd70e3d4c18b203d67386bc66fb&rev=1&e=2ozte3)
-	[Copy array with square brackets[ ]](https://uottawa.sharepoint.com/teams/uORocketry/_layouts/15/guestaccess.aspx?guestaccesstoken=ZXS1CMLSMC0we8bEqpjsxDBtVD51LhGQSyg3THvYh7w%3D&docid=2_0878db1b73934485880be4576431d311a&rev=1&e=bfH4Kh)

The lookup table takes around `14464 bytes` = `14.5kb` of memory and contains `1808 data points` = `3616 float values`.

```c++
/**
 * @param {array} arr - lookup table
 * @param {float} value - voltage in millivolts
 * @param {int} lower - index of lower limit in lookuptable
 * @param {int} upper - index of upper limit in lookuptable
 *@returns {float} temperature in °C
 */
float binarySearch(float arr[][2], float value, int lower, int upper)
{
    if (lower > upper)
    {
        return -1;
    }
    else
    {
        int mid = (lower + upper) / 2;
        if (value == arr[mid][0])
        {
            return arr[mid][1];
        }
        // if value is really close to mid. when value is between mid and value next to it => Interpolate. https://www.wallstreetmojo.com/interpolation/
        else if (value > arr[mid][0] && value < arr[mid + 1][0])
        {
            return (arr[mid][1] + ((arr[mid + 1][1] - arr[mid][1]) / (arr[mid + 1][0] - arr[mid][0])) * (value - arr[mid][0]));
        }
        // right side
        else if (value > arr[mid][0])
        {
            return binarySearch(arr, value, mid + 1, upper);
        }
        // left side
        else
        {
            return binarySearch(arr, value, lower, mid - 1);
        }
    }
}
```
## Rust Implementation
```rust
fn binary_search(arr: &[[f64; 2]; 1808], value: f64, lower: usize, upper: usize) -> f64 {
    if lower > upper {
        -1.0
    } else {
        let mid: usize = (lower + upper) / 2;

        if value == arr[mid][0] {
            arr[mid][1]
        }
        // if value is really close to mid. when value is between mid and value next to it => Interpolate. https://www.wallstreetmojo.com/interpolation/
        else if value > arr[mid][0] && value < arr[mid + 1][0] {
            arr[mid][1]
                + ((arr[mid + 1][1] - arr[mid][1]) / (arr[mid + 1][0] - arr[mid][0]))
                    * (value - arr[mid][0])
        }
        // right side
        else if value > arr[mid][0] {
            binary_search(arr, value, mid + 1, upper)
        }
        // left side
        else {
            binary_search(arr, value, lower, mid - 1)
        }
    }
}
```

