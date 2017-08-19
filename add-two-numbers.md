# Add Two Numbers

## Problem Description

You are given two**non-empty**linked lists representing two non-negative integers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

**Input:**\(2 -&gt; 4 -&gt; 3\) + \(5 -&gt; 6 -&gt; 4\)  
**Output:**7 -&gt; 0 -&gt; 8

> Companies: Amazon, Microsoft, Bloomberg, Airbnb, Adobe

## Analysis

This is not a hard one. Use a variable as a carry symbol, iterate both of those two linked lists and add each node.

## Solution

```py
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    # @param {ListNode} l1
    # @param {ListNode} l2
    # @return {ListNode}
    def addTwoNumbers(self, l1, l2):
        carry = False
        ret = result = ListNode(0)
        while l1 != None or l2 != None or carry:
            res = 0
            if l1:
                res += l1.val
                l1 = l1.next
            if l2:
                res += l2.val
                l2 = l2.next
            if carry:
                res += 1
            node = ListNode(res% 10)
            carry = res / 10
            result.next = node
            result = result.next
        return ret.next
```



