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

1. `摸索出leetcode的刷题方式，首先在脑海中考虑使用伪代码如何处理（包括用哪些函数来处理比如enumerate等），如何比较答案中的内容，看是否哪些点没有考虑到。`

2. 这里就发现本来想题中的移动来分次比较，但是没想到竟然摸索出规律：

    F(0) = 0A + 1B + 2C +3D

    F(1) = 0D + 1A + 2B +3C

    F(2) = 0C + 1D + 2A +3B

    F(3) = 0B + 1C + 2D +3A

    那么，我们通过仔细观察，我们可以得出下面的规律：

    F(1) = F(0) + sum - 4D

    F(2) = F(1) + sum - 4C

    F(3) = F(2) + sum - 4B

    那么我们就找到规律了, F(i) = F(i-1) + sum - n*A[n-i]

3. python 中德比较大小，直接用函数max()，返回给定参数的最大值，参数可以为序列，其语法为max( x, y, z, .... )

4. xrange返回一个生成器，xrange做循环的性能比range好,尤其是返回很大的时候.除非要返回一个列表,则用range。注意xrange(1,n)表示从1开始取，取不到n。

5.  python中德递归的加法缩略写法，首先写出原式样：`currentvalue = currentvalue + s - n*A[n-i]`，然后将其中重复部分略去即可：`currentvalue += s - n*A[n-i]`。
