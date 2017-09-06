# Remove Nth Node From End of List

## Problem Description

Given a linked list, remove thenthnode from the end of list and return its head.

For example,

```
Given linked list: 1->2->3->4->5, and n = 2

After removing the second node from the end, the linked list becomes 1->2->3->5.
```

**Note:**  
Givennwill always be valid.  
Try to do this in one pass.

## Analysis

This problem can be solved with two pointer, a slow pointer and a fast pointer. first make the fast pointer is n+1 place fast  forward \(To remove nth node, we need to find the node before the nth node\). Then move fast pointer to the end and maintain the gap between those two pointers.

## Solution

```py
class ListNode(object):
    def __init__(self, x):
        self.val = x
        self.next = None

class Solution(object):
    def removeNthFromEnd(self, head, n):
        """
        :type head: ListNode
        :type n: int
        :rtype: ListNode
        """
        start = ListNode(0)
        slow = start
        fast = start
        slow.next = head
        for i in xrange(n+1):
            fast = fast.next
        while fast != None:
            slow = slow.next
            fast = fast.next
        slow.next = slow.next.next
        return start.next
```



