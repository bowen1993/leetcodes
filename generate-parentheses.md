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

add left bracket, when hit max, add right bracket, when hit max, add to results. backtrace to max-1 left brackets status and add right bracket.

## Solution





