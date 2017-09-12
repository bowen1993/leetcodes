# Reverse Linked List

## Problem Description

Reverse a singly linked list.

## Analysis

use a var as previous node. or use recursive.

## Solution

**Iterative**

```py
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def reverseList(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        prev = None
        while head:
            curr = head
            head = head.next
            curr.next = prev
            prev = curr
        return prev
```

**recursive**

```py
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def reverseList(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        return self._reverseList(head)
    
    def _reverseList(self, node, prev=None):
        if not node:
            return prev
        n = node.next
        node.next = prev
        return self._reverseList(n, node)
```



