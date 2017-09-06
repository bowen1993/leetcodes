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



