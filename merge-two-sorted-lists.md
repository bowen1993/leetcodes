# Merge Two Sorted Lists

## Problem Description

Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.

> Companies: Amazon, LinkedIn, Apple, Microsoft

## Analysis

Basic Question

## Solution

```py
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def mergeTwoLists(self, l1, l2):
        """
        :type l1: ListNode
        :type l2: ListNode
        :rtype: ListNode
        """
        if l1 == None:
            return l2
        if l2 == None:
            return l1
        dummy = curr = ListNode(0)
        dummy.next = l1
        while l1 and l2:
            if l1.val < l2.val:
                l1 = l1.next
            else:
                nxt = curr.next
                curr.next = l2
                tmp = l2.next
                l2.next = nxt
                l2 = tmp
            curr = curr.next
        curr.next = l1 or l2
        return dummy.next
```



