# Question

**Given numRows, generate the first numRows of Pascal's triangle.**

# Example:

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

# Answer

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

# Knowledge：
1. 基本思路是每层保存前一行的指针，然后当前航数据根据上一行来得到，每个元素就是上一行两个相邻元素相加（第一个和最后一个元素是1）。算法时间复杂度应该是O\(1+2+3+...+n\)=O\(n^2\)，空间上只需要一个序列来存储结果，不需要额外空间。

    **注意：这个概念很关键，问自己是否需要额外空间来存储数据。**

    即从第三行开始的第n行中，共有n个数。首尾两个数为1，而第i个数（ 1 &lt; i &lt; n ）的值，则为第n-1行中第i-1个数与第i个数相加的和，用数学公式表达为：

    `N[i] = N[i-1] + N[i]`

2. **程序先考虑空间，再考虑时间**。这里可以考虑先用append每次加入一个空列表，然后再在其中append数据，这个过程是空间。而用双指针实现，则是时间。

3. **双指针问题——行列展开**。当发现有行展开，列展开时，就要用双指针了。常见用法：

    ```python
    for i in xrange(n):
        for j in xrange(i + 1):
    ```




