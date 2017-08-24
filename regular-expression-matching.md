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

**Status**:

dp\[i\]\[j\] means the match status of p\[:i\] and s\[:j\]

> dp\[0\]\[0\] means two empty strings. Here for dp\[i\]\[j\], we should use p\[i-1\] and s\[j-1\], not p\[i\] and s\[j\]

**Function**:

for dp\[i\]\[j\]:

if p\[i-1\] != '\*':  dp\[i\]\[j\] = dp\[i-1\]\[j-1\] && \(p\[i-1\] == s\[j-1\] \|\| p\[i-1\] == '.'\)

> if current p is not \*, check diagonal status and current s and p char.

if p\[i-1\] == '\*': dp\[i\]\[j\] = dp\[i-2\]\[j\] \|\| \( \(s\[j-1\] == p\[i-2\] \|\| p\[i-2\] == '.'\) && dp\[i\]\[j-1\] \)

> if current p character is \*  dp\[i\]\[j\] would be true if dp\[i-2\]\[j\] is true \(last two character in p would be x\*, which can match with empty string\). or dp\[i\]\[j-1\] is true and current s character matches last p character.

**Initialization**:

dp\[0\]\[0\] = true

for j = 0 \(s is empty\), p\[:i\] should be able to match empty string \(x\* format\)

**Answer**:

dp\[-1\]\[-1\]

#### Recursive \(with Cache\):

Mostly same as DP. Detail in Solution section.

## Solution:

#### Dynamic Programming

```py
def isMatch(s, p):
    # dp init state
    dp = [[False] * (len(s) + 1) for _ in range(len(p) + 1)]
    dp[0][0] = True

    for i in range(2, len(p) + 1):
        dp[i][0] = dp[i-2][0] and p[i-1] == '*'

    for i in range(1, len(p) + 1):
        for j in range(1, len(s) + 1):
            if p[i-1] != '*':
                dp[i][j] = dp[i-1][j-1] and \
                    (p[i-1] == s[j-1] or p[i-1] == '.')
            else:
                dp[i][j] = dp[i-2][j] or \
                    ( (s[j-1] == p[i-2] or p[i-2] == '.') and dp[i][j-1])

    return dp[-1][-1]
```

#### Recursive:

```py
cache = {}
def isMatch(s, p):
    if (s, p) in cache:
        return cache[(s, p)]
    # Both empty
    if not p:
        return not s
    if p[-1] == '*':
        if isMatch(s, p[:-2]):
            cache[(s, p)] = True
            return True
        if s and (s[-1] == p[-2] or p[-2] == '.') and isMatch(s[:-1], p):
            cache[(s, p)] = True
            return True
    if s and (s[-1] == p[-1] or p[-1] == '.') and isMatch(s[:-1], p[:-1]):
        cache[(s,p)] = True
        return True
    cache[(s,p)] = False
    return False
```



