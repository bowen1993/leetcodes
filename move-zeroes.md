# Move Zeroes

## Problem Description

Given an array`nums`, write a function to move all`0`'s to the end of it while maintaining the relative order of the non-zero elements.

For example, given`nums = [0, 1, 0, 3, 12]`, after calling your function,`nums`should be`[1, 3, 12, 0, 0]`.

**Note**:

1. You must do this **in-place **without making a copy of the array.
2. Minimize the total number of operations.

> Companies: Facebook, Bloomberg

## Analysis:

iterate the array, when a zero was found, remove it and append a zero to the end

## Solution

```py
class Solution(object):
    def moveZeroes(self, nums):
        """
        :type nums: List[int]
        :rtype: void Do not return anything, modify nums in-place instead.
        """
        for num in nums:
            if num == 0:
                nums.remove(num)
                nums.append(0)
        
```



