# 3Sum

## Problem Description

Given an arraySofnintegers, are there elementsa,b,cinSsuch thata+b+c= 0? Find all unique triplets in the array which gives the sum of zero.

**Note:**The solution set must not contain duplicate triplets.

```
For example, given array S = [-1, 0, 1, 2, -1, -4],

A solution set is:
[
  [-1, 0, 1],
  [-1, -1, 2]
]
```

## Analysis

For each element, find two other elements which sum equals negative of current element \(2Sum problem\).

## Solution

```py
def threeSum(nums):
    results = []
    if nums == None or len(nums) < 3:
        return results
    nums = sorted(nums)

    for i in xrange(len(nums)):
        if i > 0 and nums[i] == nums[i-1]:
            continue
        left = i + 1
        right = len(nums) - 1
        while left < right:
            sums = nums[i] + nums[left] + nums[right]
            if sums == 0:
                results.append([nums[i], nums[left], nums[right]])
                left += 1
                right -= 1
                while left < right and nums[left] == nums[left-1]:
                    left += 1
                while left < right and nums[right] == nums[right+1]:
                    right -= 1
            elif sums < 0:
                left += 1
            else:
                right -= 1
    return results
```



