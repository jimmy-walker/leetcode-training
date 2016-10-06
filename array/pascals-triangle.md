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

## solution：this is done by myself.

```python
class Solution(object):
    def getRow(self, rowIndex):
        """
        :type rowIndex: int
        :rtype: List[int]
        """
        result = []
        for i in xrange(rowIndex+1):
            result.append([])
            for j in xrange(i + 1):
                if j in (0, i):
                    result[i].append(1)
                else:
                    result[i].append(result[i - 1][j - 1] + result[i - 1][j])
        return result[rowIndex]
```

# Knowledge：

1. 基本思路就是利用上一次的函数，从而输出最后一行。

