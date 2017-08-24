# Longest Common Prefix

## Project Description

Write a function to find the longest common prefix string amongst an array of strings.

## Analysis

See Solution

> Companies: Yelp

## Solution

```py
def longestCommonPrefix(strs):
    prefix = ""
    if len(strs) == 0:
        return ""
    shortestIndex, shortestLength = 0, len(strs[0])
    for i in xrange(1, len(strs)):
        if shortestLength > len(strs[i]):
            shortestIndex, shortestLength = i, len(strs[i])

    for i in xrange(shortestLength):
        for index in range(len(strs)):
            if strs[index][i] != strs[shortestIndex][i]:
                return prefix
        prefix += strs[index][i]
    return prefix
```



