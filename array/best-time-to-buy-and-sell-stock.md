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
class Solution(object):
    def maxProfit(self, prices):
        """
        :type prices: List[int]
        :rtype: int
        """
        max_profit, min_price = 0, float("inf")
        for price in prices:
            min_price = min(min_price, price) #保存之前至今数据中的最小值
            max_profit = max(max_profit, price - min_price) #若数据一直变小，那么max_profit一直是0 
        return max_profit
```

## solution2: this is my answer. But it has a problem as followed.
It return the error: Time Limit Exceeded, when input is `[10000,9999,...]`. Cause its runtime is O(n^2). 由(a1 + an)\*n/2 = (n-1+1)\*(n-1)/2得到，其中从n-1次相减计算到最后两个元素1次相减计算。

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

2. python中使用如下表达式表示正负无穷：
    ```
    float("inf"), float("-inf")
    ```
3. **如果双指针的runtime超时，就考虑用单指针，另一个变量考虑在此指针代表的变量循环中实时更新。**在思考空间上已经考虑原位操作，时间上考虑单指针，那么在编程过程中，就将单指针的每次循环平行写出，**问自己每一次循环能够做什么与题目相关的工作，从而帮助形成解决方法**。比如说在第三次循环（即列表第三个位置上），就用当前位置值减去前面的最小值，保存这个差额。然后第四个循环上，重复同样操作，从而写出代码。

4. 答案的思路是只要有一个变量记录之前至今数据的最小值，那么取最大差值即可。

