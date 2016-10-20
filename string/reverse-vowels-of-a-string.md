# Question

**Write a function that takes a string as input and reverse only the vowels of a string.**

# Example:

Given s = "hello", return "holle".

Given s = "leetcode", return "leotcede".

# Hint

The vowels does not include the letter "y".

# Answer

## solution：

```python
class Solution(object):
    def reverseVowels(self, s):
        """
        :type s: str
        :rtype: str
        """
        vowels = "aeiou"
        string = list(s)
        i, j = 0, len(s) - 1
        while i < j:
            if string[i].lower() not in vowels:
                i += 1
            elif string[j].lower() not in vowels:
                j -= 1
            else:
                string[i], string[j] = string[j], string[i]
                i += 1
                j -= 1
        return "".join(string)
```

# Knowledge：

1. 一开始考虑这个问题的时候，我在思考空间上考虑多一个列表保存元音，然后利用一个新的字典保存enumerate找到的元音，但是在互换位置的时候，我遇到了困惑。原来这是一道**双指针问题——首尾靠近**。我自己在想思考时间部分中考虑到了首尾互相靠近，遇到了合适值再对换，但是不知道代码怎么编写。这说明我需要总结这方面得知识。

  ```python
   i, j = 0, len(s) - 1 #这段代码较为经典，记住它，先赋值0与N-1
   while i < j: #用while作循环，比较条件是相互大小
       if string[i].lower() not in vowels: #先去找左端点i的值，while循环找到后，再找右端点j的值
           i += 1
       elif string[j].lower() not in vowels: #找到上面的i的值后，再利用循环找右端点的值
           j -= 1
       else:
           string[i], string[j] = string[j], string[i] #双指针问题往往是原位操作
           i += 1
           j -= 1
  ```


