#Question
**Given two binary strings, return their sum (also a binary string).**

#Example
For example,
a = `"11"`
b = `"1"`
Return `"100"`.

#Answer
##solution：
```python
class Solution(object):
    def addBinary(self, a, b):
        """
        :type a: str
        :type b: str
        :rtype: str
        """
        return bin(int(a,2)+int(b,2))[2:]
```

#Knowledge：

1. 这道题目



2. 利用`if not strs`代替`if strs ==[]`。



3. 列表推导式很重要，特别是这题目中用的例子，作为**列表推导式的经典例子**学习。

 ```python

 [cprefix[0:x] for x in xrange(len(cprefix)+1,0,-1)]



 ```


