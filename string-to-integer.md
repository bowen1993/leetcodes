# String to Integer

## Problem Description

Implementatoito convert a string to an integer.

**Hint:**Carefully consider all possible input cases. If you want a challenge, please do not see below and ask yourself what are the possible input cases.

**Notes:**It is intended for this problem to be specified vaguely \(ie, no given input specs\). You are responsible to gather all the input requirements up front.

> Companies: Amazon, Microsoft, Bloomberg, Uber

## Analysis

This is a simple question.

## Solution

```py
def myAtoi(s):
    r = 0
    isNegative = False
    s = s.strip()
    if s.startswith('-') or s.startswith('+'):
        isNegative = s.startswith('-')
        s = s[1:]
    for c in s:
        try:
            newDitig = int(c)
            r = r * 10 + newDitig
        except:
            break
    if isNegative:
        r = -r
    if r > 2147483647:
        r = 2147483647
    if r < -2147483648:
        r = -2147483648
    return r
```



