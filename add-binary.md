# Add Binary

## Problem Description

Given two binary strings, return their sum \(also a binary string\).

For example,  
a =`"11"`  
b =`"1"`  
Return`"100"`

> Companies: Facebook

## Analysis

Simple Question. Use a carry variable.

## Solution

```py
def addBinary(a, b):
    """
    :type a: str
    :type b: str
    :rtype: str
    """
    carry = 0
    i, j = len(a) - 1, len(b) - 1
    res = ""
    while i >= 0 or j >= 0:
        sums = carry
        if j >= 0:
            sums += int(b[j])
            j -= 1
        if i >= 0:
            sums += int(a[i])
            i -= 1
        res = str(sums % 2) + res
        carry = sums / 2
    if carry != 0:
        res = str(carry) + res
    return res
```



