#Question
**Given a string containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.**

The brackets must close in the correct order, `"()"` and `"()[]{}"` are all valid but `"(]"` and `"([)]"` are not.

#Answer
## solution：

```python
class Solution(object):
    def isValid(self, s):
        """
        :type s: str
        :rtype: bool
        """
        stack, lookup = [], {"(": ")", "{": "}", "[": "]"}
        for parenthese in s:
            if parenthese in lookup:
                stack.append(parenthese)
            elif len(stack) == 0 or lookup[stack.pop()] != parenthese:
                return False
        return len(stack) == 0        
```

#Knowledge：
1. 这道题目是string系列的第一题，拿到后其实是懵掉了。后来网上查了后才知道这是一道经典的**利用栈判定括号匹配**的问题，**说明还需要不断累计类似题目，遇到不会的，就要去查询，看是否能够总结成一类题型**。

2. **利用栈判定括号匹配**：从左向右遍历字符串，若为左括号则压入栈（append),若为右括号则将栈顶元素与该括号进行匹配，若匹配则将该左括号出栈，若不匹配则直接返回假，遍历完成后如果栈为空则为正确括号序列，否则为不匹配括号序列。
