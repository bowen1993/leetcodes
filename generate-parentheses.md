# Generate Parentheses

## Problem Description

Givennpairs of parentheses, write a function to generate all combinations of well-formed parentheses.

For example, givenn= 3, a solution set is:

```
[
  "((()))",
  "(()())",
  "(())()",
  "()(())",
  "()()()"
]
```

> Companies: Google, Uber, Zenefits

## Analysis

This problem can be solved with backtrace method.

add left bracket, when hit max, add right bracket, when hit number of left brackets , add to results. backtrace to max-1 left brackets status and add right bracket.

## Solution

```py
def generateParenthesis(n):
    """
    :type n: int
    :rtype: List[str]
    """
    result = []
    backtrace(result, "", 0, 0, n)
    return result

def backtrace(result, s, left, right, n):
    if len(s) == n * 2:
        result.append(s)
    if left < n:
        backtrace(result, s+"(", left + 1, right, n)
    if right < left:
        backtrace(result, s+")", left, right+1, n)
```



