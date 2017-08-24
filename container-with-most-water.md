# Container With Most Water

## Problem Description

Givennnon-negative integersa1,a2, ...,an, where each represents a point at coordinate \(i,ai\).nvertical lines are drawn such that the two endpoints of lineiis at \(i,ai\) and \(i, 0\). Find two lines, which together with x-axis forms a container, such that the container contains the most water.

Note: You may not slant the container andnis at least 2.

> Companies: Bloomberg

## Analysis

This is a two pointer problem.

The volume of contained water is related to both the lowest high of two lines and distance between two lines.

To find the biggest container, we only move the lowest line each time. See proof here[^1]

[^1]: [proof of moving lines](https://aaronice.gitbooks.io/lintcode/content/two_pointers/container_with_most_water.html)

