# 4Sum

## Problem Description

Given an arraySofnintegers, are there elementsa,b,c, anddinSsuch thata+b+c+d= target? Find all unique quadruplets in the array which gives the sum of target.

**Note:**The solution set must not contain duplicate quadruplets.

```
For example, given array S = [1, 0, -1, 0, -2, 2], and target = 0.

A solution set is:
[
  [-1,  0, 0, 1],
  [-2, -1, 1, 2],
  [-2,  0, 0, 2]
]
```

## Analysis

A K Sum problem can be solved by solving K-1 Sum problem with target as target - nums\[i\], where i is index of nums.

Here for 4Sum problem, we iterate all elements in nums, with each elements, we use 3Sum to find target that euqals to target-nums\[i\]

 

