# Valid Parentheses

## Problem Description

Given a string containing just the characters`'('`,`')'`,`'{'`,`'}'`,`'['`and`']'`, determine if the input string is valid.

The brackets must close in the correct order,`"()"`and`"()[]{}"`are all valid but`"(]"`and`"([)]"`are not.

> Companies: Google Airbnb Facebook Twitter Zenefits Amazon Microsoft Bloomberg



## Analysis

This is a simple problem that can be solved with stack. Put each character into stack, once a right bracket is found, pop items until right bracket is found, or if encounter other brackets, return false.

## Solution

```py
def isValid(s):
    """
    :type s: str
    :rtype: bool
    """
    stack = []
    bracketMap = {
        ")": "(",
        "]": "[",
        "}": "{"
    }
    for char in s:
        if char in bracketMap:
            if len(stack) == 0:
                return False
            temp = stack.pop()
            if temp != bracketMap[char]:
                return False
        else:
            stack.append(char)
    return len(stack) == 0
```



