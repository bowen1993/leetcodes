# Two Sum

## Problem Description

Given an array of integers, return **indices **of the two numbers such that they add up to a specific target.

You may assume that each input would have **exactly **one solution, and you may not use thesameelement twice.

#### Example:

```
Input
nums = [2, 7, 11, 15], target = 9

Output:
[0,1]  // nums[0] + nums[1] = 9
```

## Analysis

This is a two-pointers problem, the solution is pretty straight forward.

1. sort the list.
2. Init pointers. left = 0, right = len\(nums\) - 1. if sum of nums\[left\] and nums\[right\] is bigger than target, right - 1, if smaller, left + 1.

> The result should be the original indices, here we used an array to store the original indices.

## Solution

```py
def twoSum(nums, target):
    indexes = range(len(nums))
    def comp(x, y):
        return nums[x] - nums[y]
    indexes = sorted(indexes, cmp=comp)
    left = 0
    right = len(indexes) - 1
    while left < right:
        sums = nums[indexes[left]] + nums[indexes[right]]
        if sums == target:
            return [indexes[left], indexes[right]]
        if sums < target:
            left += 1
        else:
            right -= 1
    return []
```



