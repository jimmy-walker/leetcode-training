#Question

**Say you have an array for which the ith element is the price of a given stock on day i.**

If you were only permitted to complete at most one transaction (ie, buy one and sell one share of the stock), design an algorithm to find the maximum profit.

#Example
```
Input: [7, 1, 5, 3, 6, 4]
Output: 5

max. difference = 6-1 = 5 (not 7-1 = 6, as selling price needs to be larger than buying price)
```
```
Input: [7, 6, 4, 3, 1]
Output: 0

In this case, no transaction is done, i.e. max profit = 0.
```

#Answer

## solution1：
```python
class
```

## solution2: this is my answer. but it return the error: Time Limit Exceeded, when input is `[10000,9999,...]`. Cause its runtime is O(n^2). 由(a1 + an)*n/2 = (n-1+1)*(n-1)/2得到，其中从n-1次相减计算到最后两个元素1次相减计算。

```python
class Solution(object):
    def maxProfit(self, prices):
        """
        :type prices: List[int]
        :rtype: int
        """
        max_profit = 0
        for i in xrange(len(prices)):
            for j in xrange(i,len(prices)):
                cur_profit = prices[j] - prices[i]
                max_profit = max(max_profit,cur_profit)
        return max_profit
```

#Knowledge：

1. 这道题目提醒了我要注意runtime的限制，我本来的方案可以在短的列表上实验成功，但是runtime有O(n^2)，所以还是不用此方法了。

2. 

