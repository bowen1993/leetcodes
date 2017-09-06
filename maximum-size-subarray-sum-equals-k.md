# Maximum Size Subarray Sum Equals k

## Problem Description

Given an arraynumsand a target valuek, find the maximum length of a subarray that sums tok. If there isn't one, return 0 instead.

**Note:**  
The sum of the entirenumsarray is guaranteed to fit within the 32-bit signed integer range.

**Example 1:**  


Givennums=`[1, -1, 5, -2, 3]`,k=`3`,  
return`4`. \(because the subarray`[1, -1, 5, -2]`sums to 3 and is the longest\)

**Example 2:**  


Givennums=`[-2, -1, 2, 1]`,k=`1`,  
return`2`. \(because the subarray`[-1, 2]`sums to 1 and is the longest\)

**Follow Up:**  
Can you do it in O\(n\) time?



> Companies: Lalantir, Facebook



## Analysis

Iterate the array. use a hashmap to store accumulative value. Key would be the accumulate, value would be the index.

Then try to find accumulate - k in hashmap. If found, check whether it is the largest.

## Solution





