# Best Time to Buy and Sell Stock

## Problem Description

Say you have an array for which theithelement is the price of a given stock on dayi.

If you were only permitted to complete at most one transaction \(ie, buy one and sell one share of the stock\), design an algorithm to find the maximum profit.

**Example 1:**

```
Input: [7, 1, 5, 3, 6, 4]
Output: 5

max. difference = 6-1 = 5 (not 7-1 = 6, as selling price needs to be larger than buying price)

```

**Example 2:**

```
Input: [7, 6, 4, 3, 1]
Output: 0

In this case, no transaction is done, i.e. max profit = 0.
```

> Companies: Facebook, Microsoft, Amazon, Bloomberg, Uber



## Analysis

iterate the array. use a variable as current holding stock. when current value is smaller than current holding, change holding to current value. compare current value with maxprofit.

## Solution

```py
class Solution(object):
    def maxProfit(self, prices):
        """
        :type prices: List[int]
        :rtype: int
        """
        if len(prices) == 0:
            return 0
        maxProfit = 0
        holding = prices[0]
        for i in range(1, len(prices)):
            profit = prices[i] - holding
            if profit > maxProfit:
                maxProfit = profit
            if prices[i] < holding:
                holding = prices[i]
        return maxProfit
```



