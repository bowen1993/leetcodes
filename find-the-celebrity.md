# Find the Celebrity

## Problem Description

Suppose you are at a party with`n`people \(labeled from`0`to`n - 1`\) and among them, there may exist one celebrity. The definition of a celebrity is that all the other`n - 1`people know him/her but he/she does not know any of them.

Now you want to find out who the celebrity is or verify that there is not one. The only thing you are allowed to do is to ask questions like: "Hi, A. Do you know B?" to get information of whether A knows B. You need to find out the celebrity \(or verify there is not one\) by asking as few questions as possible \(in the asymptotic sense\).

You are given a helper function`bool knows(a, b)`which tells you whether A knows B. Implement a function`int findCelebrity(n)`, your function should minimize the number of calls to`knows`.

**Note**: There will be exactly one celebrity if he/she is in the party. Return the celebrity's label if there is a celebrity in the party. If there is no celebrity, return`-1`.

> Companies: LinkedIn, Facebook

## Analysis

To reduce times of calling knows\(\). We should eliminate impossible people and find a candidate. The celebrity knows nobody and everybody knows the celebrity. We start from 0 as candidate, if 0 knows 1, 0 can not be celebrity, 1 might, so 1 as candidate. If 1 does not know 2, 1 still as candidate, 2 is not. if 1 knows 3, 3 as candidate. Loop to n, we found only possible candidate x. Then we check x.

## Solution

```py
# The knows API is already defined for you.
# @param a, person a
# @param b, person b
# @return a boolean, whether a knows b
# def knows(a, b):

class Solution(object):
    def findCelebrity(self, n):
        """
        :type n: int
        :rtype: int
        """
        x = 0
        for i in xrange(n):
            if knows(x, i):
                x = i
        for i in xrange(x):
            if knows(x, i):
                return -1
        for i in xrange(n):
            if not knows(i, x):
                return -1
        return x
```



