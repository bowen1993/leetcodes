# Longest Palindromic Substring

## Problem Description

Given a string**s**, find the longest palindromic substring in**s**. You may assume that the maximum length of**s**is 1000.

**Example:**

```
Input:
 "babad"


Output:
 "bab"


Note:
 "aba" is also a valid answer.
```

**Example:**

```
Input:
 "cbbd"


Output:
 "bb"
```

> Companies: Amazon, Microsoft, Bloomberg

## Analysis

#### Dynamic Programming

Time: O\(N^2\) Space: O\(n^2\)

This problem can be solved by Dynamic Programming method.

Here we use 2-d array dp to store status. dp\[i\]\[j\] means whether s\[i:j\] is a palindromic string or not.

