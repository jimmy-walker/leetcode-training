#Question
**Implement strStr()**.
Returns the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.

#Answer
##solution：this is done by meself
```python
class Solution(object):
    def strStr(self, haystack, needle):
        """
        :type haystack: str
        :type needle: str
        :rtype: int
        """
        for i in xrange(0,len(haystack)-len(needle)+1):
            if haystack[i:i+len(needle)] == needle:
                return i
        return -1
```
#Knowledge：
1. 这道题目调试了一会，后来想到了编程部分就好了。在编程部分，用具体例子来实现，比如"pi"与"missssispi"从而定下循环值。
