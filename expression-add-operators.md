# Expression Add Operators

## Problem Description

Given a string that contains only digits`0-9`and a target value, return all possibilities to add**binary**operators \(not unary\)`+`,`-`, or`*`between the digits so they evaluate to the target value.

Examples:

```
"123", 6 -> ["1+2+3", "1*2*3"] 
"232", 8 -> ["2*3+2", "2+3*2"]
"105", 5 -> ["1*0+5","10-5"]
"00", 0 -> ["0+0", "0-0", "0*0"]
"3456237490", 9191 -> []
```

> Companies: Google, Facebook

## Analysis

DFS

## Solution

```py
class Solution(object):
    def addOperators(self, num, target):
        """
        :type num: str
        :type target: int
        :rtype: List[str]
        """
        self.res = []
        if num is None or len(num) == 0:
            return self.res
        self.dfs(num, "", 0, 0, 0, target)
        return self.res

        
    def dfs(self, num, path, pos, temp_res, multed, target):
        if pos == len(num):
            if target == temp_res:
                self.res.append(path)
                return
        for i in range(pos, len(num)):
            if i != pos and num[pos] == '0':
                break
            curr = int(num[pos:i+1])
            if pos == 0:
                self.dfs(num, path + str(curr), i+1, curr, curr, target)
            else:
                self.dfs(num, path + "+" + str(curr), i+1, temp_res + curr, curr, target)
                self.dfs(num, path + "-" + str(curr), i+1, temp_res - curr, -curr, target)
                self.dfs(num, path + "*" + str(curr), i+1, temp_res - multed + multed * curr, multed * curr, target)
```





