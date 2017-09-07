# Decode Ways

## Problem Description

A message containing letters from`A-Z`is being encoded to numbers using the following mapping:

```
'A' -> 1
'B' -> 2
...
'Z' -> 26
```

Given an encoded message containing digits, determine the total number of ways to decode it.

For example,  
Given encoded message`"12"`, it could be decoded as`"AB"`\(1 2\) or`"L"`\(12\).

The number of ways decoding`"12"`is 2.

> Companies: Microsoft, Uber, Facebook

## Analysis

This problem can be solved with Dynamic Programming

dp\[i\] means number of decode ways for string s\[0:i\]. 

dp\[0\] = 1 for an empty string only have one decode way

dp\[1\] = 1 if s\[0\] != 0 else 0

dp\[n\] = dp\[n-1\] + dp\[n-2\] if s\[n\] can combine with s\[n-1\]



