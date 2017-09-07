# Binary Tree Vertical Order Traversal

Given a binary tree, return thevertical ordertraversal of its nodes' values. \(ie, from top to bottom, column by column\).

If two nodes are in the same row and column, the order should be from**left to right**.

**Examples:**  




1. Given binary tree
   `[3,9,20,null,null,15,7]`
   ,
 
   ```
      3
     /\
    /  \
    9  20
       /\
      /  \
     15   7

   ```



   return its vertical order traversal as:  


   ```
   [
     [9],
     [3,15],
     [20],
     [7]
   ]

   ```

2. Given binary tree
   `[3,9,8,4,0,1,7]`
   ,
 
   ```
        3
       /\
      /  \
      9   8
     /\  /\
    /  \/  \
    4  01   7

   ```



   return its vertical order traversal as:  


   ```
   [
     [4],
     [9],
     [3,0,1],
     [8],
     [7]
   ]

   ```

3. Given binary tree
   `[3,9,8,4,0,1,7,null,null,null,2,5]`
   \(0's right child is 2 and 1's left child is 5\),
 
   ```
        3
       /\
      /  \
      9   8
     /\  /\  /  \/  \
    4  01   7
       /\
      /  \
      5   2

   ```



   return its vertical order traversal as:  


   ```
   [
     [4],
     [9,5],
     [3,0,1],
     [8,2],
     [7]
   ]

   ```

> Companies: Google, Snapchat, Facebook



## Analysis

This problem can be solved with BFS and hashmap. Use a hashmap to store column number and value. Start with root and column number 0. For left node, column number -1, for right node, +1

## Solution 

```py
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def verticalOrder(self, root):
        """
        :type root: TreeNode
        :rtype: List[List[int]]
        """
        cols = dict()
        queue = [(root, 0)]
        for node, index in queue:
            if node:
                if index in cols:
                    cols[index].append(node.val)
                else:
                    cols[index] = [node.val]
                queue.append((node.left, index - 1))
                queue.append((node.right, index + 1))
        return [cols[i] for i in sorted(cols)]
```



