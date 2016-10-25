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
