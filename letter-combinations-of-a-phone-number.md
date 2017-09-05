# Letter Combinations of a Phone Number

## Problem Description

Given a digit string, return all possible letter combinations that the number could represent.

A mapping of digit to letters \(just like on the telephone buttons\) is given below.

![](http://upload.wikimedia.org/wikipedia/commons/thumb/7/73/Telephone-keypad2.svg/200px-Telephone-keypad2.svg.png)

```
Input:
Digit string "23"

Output:
 ["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"].
```

**Note:**  
Although the above answer is in lexicographical order, your answer could be in any order you want.

> Companies: Amazon, Dropbox, Google, Uber, Facebook

## Analysis

This problem can be solved with dfs/backtrace.

## Solution

```py
def letterCombinations(digits):
    """
    :type digits: str
    :rtype: List[str]
    """
    if len(digits) == 0:
        return []
    digitMap = {
        "2": "abc", 
        "3": "def",
        "4": "ghi",
        "5": "jkl",
        "6": "mno",
        "7": "pqrs",
        "8": "tuv",
        "9": "wxyz"
    }
    result = []
    dfs(digits, digitMap, 0, "", result)
    return result

def dfs(digits, digitMap, index, path, result):
    if len(path) == len(digits):
        result.append(path)
        return
    for i in xrange(index, len(digits)):
        for j in digitMap[digits[i]]:
            dfs(digits, digitMap, i+1, path+j, result)

print letterCombinations("23")
```



