# 3Sum Closest

## Problem Description

Given an arraySofnintegers, find three integers inSsuch that the sum is closest to a given number, target. Return the sum of the three integers. You may assume that each input would have exactly one solution.

```
    For example, given array S = {-1 2 1 -4}, and target = 1.

    The sum that is closest to the target is 2. (-1 + 2 + 1 = 2).
```

> Companies: Bloomberg

## Analysis

Similar to 3Sum. See Solution Section.

## Solution

```py
import sys
def threeSumClosest(nums, target):
    if nums == None or len(nums) < 3:
        return []
    nums = sorted(nums)
    minSum = -sys.maxint
    length = len(nums)
    for i in xrange(length - 2):
        left = i + 1
        right = length - 1
        while left < right:
            sums = nums[i] + nums[left] + nums[right]
            if sums == target:
                return sums
            elif sums < target:
                left += 1
            else:
                right -=1
            if abs(sums - target) < abs(minSum - target):
                minSum = sums
    return minSum
```



