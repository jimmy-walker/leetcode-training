#Question

**Given an array of integers `A` and let n to be its length.**

Assume `Bk` to be an array obtained by rotating the array `A` k positions clock-wise, we define a "rotation function" `F` on `A` as follow:

`F(k) = 0 * Bk[0] + 1 * Bk[1] + ... + (n-1) * Bk[n-1]`.

Calculate the maximum value of `F(0), F(1), ..., F(n-1)`.

#Example:

```
A = [4, 3, 2, 6]

F(0) = (0 * 4) + (1 * 3) + (2 * 2) + (3 * 6) = 0 + 3 + 4 + 18 = 25
F(1) = (0 * 6) + (1 * 4) + (2 * 3) + (3 * 2) = 0 + 4 + 6 + 6 = 16
F(2) = (0 * 2) + (1 * 6) + (2 * 4) + (3 * 3) = 0 + 6 + 8 + 9 = 23
F(3) = (0 * 3) + (1 * 2) + (2 * 6) + (3 * 4) = 0 + 2 + 12 + 12 = 26

So the maximum value of F(0), F(1), F(2), F(3) is F(3) = 26.
```

#Hint

n is guaranteed to be less than 10<SUP>5</SUP>.

#Answer

## solution：

```python

class Solution(object):
    def maxRotateFunction(self, A):
        """
        :type A: List[int]
        :rtype: int
        """
        n = len(A)
        s = sum(A)
        currentvalue = 0
        for i, num in enumerate(A):
            currentvalue += i*num
        maxvalue = currentvalue
        for i in xrange(1,n+1):
            currentvalue += s - n*A[n-i]
            #currentvalue = currentvalue + s - n*A[n-i]
            #F(i) = F(i-1) + sum - n*A[n-i]
            maxvalue=max(currentvalue,maxvalue)
        return maxvalue
```

#Knowledge：

1. 摸索出leetcode的刷题方式，首先在脑海中考虑使用伪代码如何处理，
在python中 None,  False, 空字符串"", 0, 空列表[], 空字典{}, 空元组()都相当于False ，即：

```python

not None == not False == not '' == not 0 == not [] == not {} == not ()

```

   注意：[0]不是False。

   `if x is not None是最好的写法，清晰，不会出现错误，以后坚持使用这种写法。`

2. Python中的%是求余，特别是用于循环时涉及到的两个数之间可能原较小数k比n大的情况：k = k % n

3. nums[:k], nums[k:] = nums[-k:], nums[:-k] 交换两段数据，注意这种用法，不要顾忌不使用第三方会影响数据保存

4. python索引，正数索引[0:n-1]；使用负数索引时，Python会从右边，也就是从最后 1 个元素开始计数。最后 1 个元素的位置编号是-1。[-n:-1]。

    

   `第1个索引的元素是包含在分片内的，而第2个则不包含在分片内。`

   

   `如果分片中最左边的索引比它右边的晚出现在序列中，结果就是一个空的序列。numbers[-3:0]，结果为[]`

