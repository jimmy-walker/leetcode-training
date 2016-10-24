#Question
Each letter in the magazine string can only be used once in your note. 

#Example
```
canConstruct("a", "b") -> false
canConstruct("aa", "ab") -> false
canConstruct("aa", "aab") -> true
```

#Hint
You may assume that both strings contain only lowercase letters.

#Answer
##solution：
```python
class Solution(object):
    def canConstruct(self, ransomNote, magazine):
        """
        :type ransomNote: str
        :type magazine: str
        :rtype: bool
        """
        ransom = list(ransomNote)
        mag = list(magazine)
        for i in ransom:
            if i in mag:
                mag.remove(i)
            else:
                return False
        return True
```
#Knowledge：
1. 还是一样使用高级语言的特点，remove删除第一个元素。

2. 这次给我的启示是需要**在思考和编程时以数据结构来思考，这样自然会想到方法**，比如remove删除。

3. 最后意外发现gitbook屏蔽关键词，返回错误：SyntaxError: Unexpected token ILLEGAL!!!