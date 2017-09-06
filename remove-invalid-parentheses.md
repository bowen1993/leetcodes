# Remove Invalid Parentheses

## Problem Description

Remove the minimum number of invalid parentheses in order to make the input string valid. Return all possible results.

Note: The input string may contain letters other than the parentheses`(`and`)`.

**Examples:**  


```
"()())()" -> ["()()()", "(())()"]
"(a)())()" -> ["(a)()()", "(a())()"]
")(" -> [""]
```

> Companies: Facebook

## Analysis

This problem can be solved with BFS method. First generate all possible strings by removing one "\(" or "\)", if valid add to result and finish. Otherwise, add to a queen and remove again.



## Solution

```py
def removeInvalidParentheses(s):
    """
    :type s: str
    :rtype: List[str]
    """
    def isValid(s):
        count = 0
        for c in s:
            if c == '(':
                count += 1
            if c == ')':
                count -= 1
                if count < 0:
                    return False
        return count == 0

    result = []
    if s == None:
        return result
    level = {s}
    while True:
        valid = filter(isValid, level)
        if valid:
            return valid
        level = {s[:i] + s[i+1:] for s in level for i in xrange(len(s))}
    return result
```



