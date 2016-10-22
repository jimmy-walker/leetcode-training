#Question
**Write a function to find the longest common prefix string amongst an array of strings.**

#Answer
##solution：this code without algorithm is done by myself.

```python
class Solution(object):
    def longestCommonPrefix(self, strs):
        """
        :type strs: List[str]
        :rtype: str
        """
        if not strs:
            return ""
        cprefix = strs[0]
        common = [cprefix[0:x] for x in xrange(len(cprefix)+1,0,-1)]
        for i in common:
            lcommon = True
            for s in strs:
                if i in s[0:len(i)]:
                    continue
                else:
                    lcommon = False
                    break
            if lcommon == True:
                return i
        return ""  
```

#Knowledge：

1. 这道题目一开始也是没有看懂什么意思，网上查了解释和想法后才明白：既然是公共子串，那每个字符串肯定都包含有，并且在头部，首先把第一个字符串作为默认最大，然后依次与后边每一个字符串对比，计算所有的最大匹配长度，长度最小的就是**。自己在知道算法后的编程已经有所提高，具体编程都是自己完成，已经能够配合本地ipython程序调试了**。

2. 利用`if not strs`代替`if strs ==[]`。

3. 列表推导式很重要，特别是这题目中用的例子，作为**列表推导式的经典例子**学习。
    ```python
    [cprefix[0:x] for x in xrange(len(cprefix)+1,0,-1)]

    ```
