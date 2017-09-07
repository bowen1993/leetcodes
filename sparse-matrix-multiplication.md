# Sparse Matrix Multiplication

## Problem Description

Given two[sparse matrices](https://en.wikipedia.org/wiki/Sparse_matrix)**A**and**B**, return the result of**AB**.

You may assume that**A**'s column number is equal to**B**'s row number.

**Example:**

```
A = [
  [ 1, 0, 0],
  [-1, 0, 3]
]

B = [
  [ 7, 0, 0 ],
  [ 0, 0, 0 ],
  [ 0, 0, 1 ]
]

     |  1 0 0 |   | 7 0 0 |   |  7 0 0 |
AB = | -1 0 3 | x | 0 0 0 | = | -7 0 3 |
                  | 0 0 1 |
```

> Companies: Facebook, LinkedIn

## Analysis

Basic Matrix Multiplication. Skip when zero

## Solution

```py
def multiply(A, B):
    """
    :type A: List[List[int]]
    :type B: List[List[int]]
    :rtype: List[List[int]]
    """
    if A is None or B is None:
        return None
    m, n, x = len(A), len(A[0]), len(B[0])
    res = [[0 for _ in range(x)] for _ in range(m)]
    for i, row in enumerate(A):
        for j, eleA in enumerate(row):
            if eleA:
                for k, eleB in enumerate(B[j]):
                    if eleB:
                        res[i][k] += eleA * eleB
    return res
```



