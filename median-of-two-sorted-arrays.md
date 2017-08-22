# Median of Two Sorted Arrays

## Problem Description

There are two sorted arrays **nums1**and **nums2**of size m and n respectively.

Find the median of the two sorted arrays. The overall run time complexity should be O\(log \(m+n\)\).

**Example 1:**

```
nums1 = [1, 3]
nums2 = [2]

The median is 2.0
```

**Example 2:**

```
nums1 = [1, 2]
nums2 = [3, 4]

The median is (2 + 3)/2 = 2.5
```

> Companies: Google, Zenefits, Microsoft, Apple, Yahoo, Dropbox, Adobe

## Analysis

For an array a with length n, the median would a\[n/2 + 1\] \(n is odd\) or \(a\[n/2\] + a\[n/2 + 1\]\) / 2 \(n is even\). Here if we can find kth smallest value in two arrays, then we can find the median.

To find the kth smallest number in two arrays, A and B.

First, we compare A\[k/2\] and B\[k/2\], if A\[k/2\] &gt; B\[k/2\], then that number will not be in the first numbers in array B, so we can remove the first k/2 numbers from B, and find \(k - k/2\)th smallest number in those remaining numbers. If k/2 is bigger than the size of a array, then the kth number would not be in the first k/2 numbers in the other array. Recursively, we can find kth number.

 

