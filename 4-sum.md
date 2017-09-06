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

## Solution

```py
def fourSum(nums, target):
    """
    :type nums: List[int]
    :type target: int
    :rtype: List[List[int]]
    """
    result = []
    if nums is None or len(nums) == 0:
        return result
    nums = sorted(nums)
    for i in xrange(len(nums)):
        if i > 0 and nums[i] == nums[i-1]:
            continue
        tempResult = threeSum(nums, target-nums[i], i+1)
        print tempResult
        for j in tempResult:
            j.append(nums[i])
            result.append(j)
    return result

def threeSum(nums, target, start):
    res = []
    for i in xrange(start, len(nums)):
        if i > start and nums[i] == nums[i-1]:
            continue
        left = i + 1
        right = len(nums) - 1
        while left < right:
            sums = nums[i] + nums[left] + nums[right]
            if sums == target:
                res.append([nums[i], nums[left], nums[right]])
                left += 1
                right -= 1
                while left < right and nums[left] == nums[left-1]:
                    left += 1
                while left < right and nums[right] == nums[right+1]:
                    right -= 1
            elif sums < target:
                left += 1
            else:
                right -= 1
    return res

print fourSum([-1,-5,-5,-3,2,5,0,4], -7)
```



