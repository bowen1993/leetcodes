# Median of Two Sorted Arrays

## Problem Description

There are two sorted arrays**nums1**and**nums2**of size m and n respectively.

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

For an array a with length n, the median would a\[n/2 + 1\] \(n is odd\) or \(a\[n/2\] + a\[n/2 + 1\]\) / 2 \(n is even\).



