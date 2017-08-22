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

For each dp\[i\]\[j\], the value would be:

dp\[i\]\[j\] = s\[i\] == s\[j\] && \(j - i &lt;= 2 \|\| dp\[i+1\]\[j-1\]\)

Then if we found max value of j - i + 1, we found the longest palindromic substring.



#### Manchester Algorithm



## Solution

```py
def longestPalindrome(s):
    if len(s) == 0:
        return None
    if len(s) == 1:
        return s

    longest = s[0:1]
    length = len(s)
    maxLen = 1
    dp = [[False for _ in xrange(length)] for __ in xrange(length)]

    for k in xrange(length):
        for i in xrange(length - k):
            j = i + k
            if s[i] == s[j] and (j - i <= 2 or dp[i+1][j-1]):
                dp[i][j] = True

                if j - i + 1 > maxLen:
                    maxLen = j - i + 1
                    longest = s[i:j+1]

    return longest
```



