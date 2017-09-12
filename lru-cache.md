# LRU Cache

## Problem Description

Design and implement a data structure for[Least Recently Used \(LRU\) cache](https://en.wikipedia.org/wiki/Cache_replacement_policies#LRU). It should support the following operations:`get`and`put`.

`get(key)`- Get the value \(will always be positive\) of the key if the key exists in the cache, otherwise return -1.  
`put(key, value)`- Set or insert the value if the key is not already present. When the cache reached its capacity, it should invalidate the least recently used item before inserting a new item.

**Follow up:**  
Could you do both operations in**O\(1\)**time complexity?

**Example:**

```
LRUCache cache = new LRUCache( 2 /* capacity */ );

cache.put(1, 1);
cache.put(2, 2);
cache.get(1);       // returns 1
cache.put(3, 3);    // evicts key 2
cache.get(2);       // returns -1 (not found)
cache.put(4, 4);    // evicts key 1
cache.get(1);       // returns -1 (not found)
cache.get(3);       // returns 3
cache.get(4);       // returns 4
```

> Companies: Google, Facebook, Microsoft, Amazon, Bloomberg, Uber, Twitter, Snapchat, Zenefits, Yahoo, Palantir

## Analysis

Use a linked list. For both get and put, move accessed item to the tail of the list

## Solution

```
class LRUCache(object):
    class Node(object):
        def __init__(self,key,value):
            self.key = key
            self.value = value
            self.prev = None
            self.next = None


    def __init__(self, capacity):
        """
        :type capacity: int
        """
        self.capacity = capacity
        self.hm = {}
        self.head = LRUCache.Node(-1,-1)
        self.tail = LRUCache.Node(-1,-1)
        self.head.next = self.tail
        self.tail.prev = self.head
        

    def get(self, key):
        """
        :rtype: int
        """
        if key not in self.hm:
            return -1
        curr = self.hm[key]
        curr.prev.next = curr.next
        curr.next.prev = curr.prev
        self.moveToTail(curr)
        return curr.value
        

    def set(self, key, value):
        """
        :type key: int
        :type value: int
        :rtype: nothing
        """
        if self.get(key) != -1:
            self.hm[key].value = value
            return
        if len(self.hm) == self.capacity:
            del self.hm[self.head.next.key]
            self.head.next = self.head.next.next
            self.head.next.prev = self.head
        node = LRUCache.Node(key,value)
        self.moveToTail(node)
        self.hm[key] = node

    def moveToTail(self,node):
        node.next = self.tail
        self.tail.prev.next = node
        node.prev = self.tail.prev
        self.tail.prev = node
        
```



