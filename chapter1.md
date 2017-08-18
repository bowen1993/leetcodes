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

> Companies: LinkedIn, Uber, Airbnb, Facebook, Amazon, Microsoft, Apple, Yahoo, Dropbox, Bloomberg, Yelp, Adobe

## Analysis

#### Two Pointers

This is a two-pointers problem, the solution is pretty straight forward.

1. sort the list.
2. Init pointers. left = 0, right = len\(nums\) - 1. if sum of nums\[left\] and nums\[right\] is bigger than target, right - 1, if smaller, left + 1.

> The result should be the original indices, here we used an array to store the original indices.

#### Hash

This problem could also be solved with hash \(for nums\[i\], storing index of other half of the target\). Details in the code.

## Solution

#### Two Pointers

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

#### Hash

```py
def twoSum(nums, target):
    if len(nums) < 2:
        return []
    buff_dict = {}
    for i in xrange(len(nums)):
        if nums[i] in buff_dict:
            return [buff_dict[nums[i]], i]
        else:
            buff_dict[target - nums[i]] = i
    return []
```



