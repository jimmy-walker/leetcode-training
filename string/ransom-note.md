#Question
**Given  an  arbitrary  ransom  note  string  and  another  string  containing  letters from  all  the  magazines,  write  a  function  that  will  return  true  if  the  ransom   note  can  be  constructed  from  the  magazines ;  otherwise,  it  will  return  false.**   

Each  letter  in  the  magazine  string  can  only  be  used  once  in  your  ransom  note.

#Example:

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
1. 还是老方法，使用python语言的高级特性，remove删除第一个元素。
2. 给我的启示是，我在思考和编程阶段，就将str当作具体的数据结构来思考，比如list存储，那么就每次删除一个，就可以实现判断功能。