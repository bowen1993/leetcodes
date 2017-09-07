# Serialize and Deserialize Binary Tree

## Project Description

Serialization is the process of converting a data structure or object into a sequence of bits so that it can be stored in a file or memory buffer, or transmitted across a network connection link to be reconstructed later in the same or another computer environment.

Design an algorithm to serialize and deserialize a binary tree. There is no restriction on how your serialization/deserialization algorithm should work. You just need to ensure that a binary tree can be serialized to a string and this string can be deserialized to the original tree structure.

For example, you may serialize the following tree

```
    1
   / \
  2   3
     / \
    4   5
```

as

`"[1,2,3,null,null,4,5]"`

, just the same as

[how LeetCode OJ serializes a binary tree](https://leetcode.com/faq/#binary-tree)

. You do not necessarily need to follow this format, so please be creative and come up with different approaches yourself.

**Note:**Do not use class member/global/static variables to store states. Your serialize and deserialize algorithms should be stateless.

> Companies: LinkedIn, Google, Uber, Facebook, Amazon, Microsoft, Yahoo, Bloomberg

## Analysis

Use format of LeetCode serialize. Recursively serialize/deserialize.

## Solution

```py
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Codec:

    SEPARATOR = ","

    def serialize(self, root):
        """Encodes a tree to a single string.
        
        :type root: TreeNode
        :rtype: str
        """
        if root is None:
            return ""
        return self.SEPARATOR.join([str(root.val), self.serialize(root.left), self.serialize(root.right)])
        

    def deserialize(self, data):
        """Decodes your encoded data to tree.
        
        :type data: str
        :rtype: TreeNode
        """
        if not data:
            return None
        return self._deserialize_list(data.split(self.SEPARATOR))

    def _deserialize_list(self, data):
        if not data:
            return None
        val = data.pop(0)
        if not val:
            return None
        node = TreeNode(val)
        node.left = self._deserialize_list(data)
        node.right = self._deserialize_list(data)
        return node
        
```



