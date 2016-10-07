# Question

**Given a sorted array, remove the duplicates in place such that each element appear only once and return the new length.**

Do not allocate extra space for another array, you must do this in place with constant memory.

# Example:

For example,
Given input array nums = `[1,1,2]`,

Your function should return length = `2`, with the first two elements of nums being `1` and `2` respectively. It doesn't matter what you leave beyond the new length.

# Answer

## solution1：

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

## solution2：this method which I wanna use is not accepted, cause it used extra space, which is not allowed.

```python
class Solution:
    def removeDuplicates(self, A):
        A = list(set(A))
        return len(A)
```

# Knowledge：

1. list与set间转换，用set(A)即可。注意定义时也是用set(list A)的形式来定义集合的。

2. 

