# Longest Substring Without Repeating Characters

## Problem Description

Given a string, find the length of the**longest substring**without repeating characters.

**Examples:**

Given`"abcabcbb"`, the answer is`"abc"`, which the length is 3.

Given`"bbbbb"`, the answer is`"b"`, with the length of 1.

Given`"pwwkew"`, the answer is`"wke"`, with the length of 3. Note that the answer must be a**substring**,`"pwke"`is asubsequenceand not a substring.

> companies: Amazon, Adobe, Bloomberg, Yelp

## Analysis

This is a two-pointer problem. It can be solved with sliding window. 

The template for sliding window:

```py
j = 0
for i in range(n):
    while j < n:
        if condition satisified :
            j++
            # update state
        else:
            break
    #update i state
```



