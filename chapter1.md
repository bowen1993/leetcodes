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

> The result should be the original indices, if we sorted the list

## Solution

```py
def twoSum(nums, target):
    indices = 
```




