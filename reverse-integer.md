# Reverse Integer

## Problem Description

Reverse digits of an integer.

**Example1:**x = 123, return 321  
**Example2:**x = -123, return -321

**Note: **The input is assumed to be a 32-bit signed integer. Your function should **return 0 when the reversed integer overflows**.

> Companies: Apple, Bloomberg

## Analysis

Easy question.Use % to get each digit.

If the result is bigger than 32-bit signed integer \(2147483647\) , return 0.

## Solution

```py
def reverse(x):
    isNeg = x < 0
    if isNeg:
        x = -x
    r = 0
    while x != 0:
        last = x % 10
        x = x / 10
        r = r * 10 + last
    if isNeg:
        r = -r
    if r < -2147483647 or r > 2147483647:
        r = 0
    return r
```



