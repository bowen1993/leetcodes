# Regular Expression Matching

## Problem Description

Implement regular expression matching with support for`'.'`and`'*'`.

```
'.' Matches any single character.
'*' Matches zero or more of the preceding element.

The matching should cover the entire input string (not partial).

The function prototype should be:
bool isMatch(const char *s, const char *p)

Some examples:
isMatch("aa","a") → false
isMatch("aa","aa") → true
isMatch("aaa","aa") → false
isMatch("aa", "a*") → true
isMatch("aa", ".*") → true
isMatch("ab", ".*") → true
isMatch("aab", "c*a*b") → true
```

> Companies: Google, Uber, Airbnb, Facebook, Twitter

## Analysis

#### Dynamic Programming

Status:

dp\[i\]\[j\] means the match status of p\[:i\] and s\[:j\]

> dp\[0\]\[0\] means two empty strings. Here for dp\[i\]\[j\], we should use p\[i-1\] and s\[j-1\], not p\[i\] and s\[j\]





