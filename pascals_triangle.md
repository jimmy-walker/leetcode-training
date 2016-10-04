#Question

**Given numRows, generate the first numRows of Pascal's triangle.**

#Example:
For example, given numRows = 5,
Return

```
[
     [1],
    [1,1],
   [1,2,1],
  [1,3,3,1],
 [1,4,6,4,1]
]
```

#Answer

## solution：

```python
class Solution(object):
    def generate(self, numRows):
        """
        :type numRows: int
        :rtype: List[List[int]]
        """
        result = []
        for i in xrange(numRows):
            result.append([])
            for j in xrange(i + 1):
                if j in (0, i):
                    result[i].append(1)
                else:
                    result[i].append(result[i - 1][j - 1] + result[i - 1][j])
        return result    
```

#Knowledge：

1. `摸索出leetcode的刷题方式，首先在脑海中考虑使用伪代码如何处理（包括用哪些函数来处理比如enumerate等），如何比较答案中的内容，看是否哪些点没有考虑到，再自己根据伪代码动手实现。`

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

3. python 中比较大小，直接用函数max()，返回给定参数的最大值，参数可以为序列，其语法为max( x, y, z, .... )

4. xrange返回一个生成器
，xrange做循环的性能比range好,尤其是返回很大的时候.除非要返回一个列表,则用range。注意xrange(1,n)表示从1开始取，取不到n。

5.  python中递归的加法缩略写法，首先写出原式样：`currentvalue = currentvalue + s - n*A[n-i]`，然后将其中重复部分略去即可：`currentvalue += s - n*A[n-i]`。在头脑中有这样一个缩略的动态过程即可，省略= currentvalue +，从而变成+=。


