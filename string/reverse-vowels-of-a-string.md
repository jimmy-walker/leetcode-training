#Question
**Write a function that takes a string as input and reverse only the vowels of a string.**

#Example:
Given s = "hello", return "holle".

Given s = "leetcode", return "leotcede".

#Hint
The vowels does not include the letter "y".

#Answer
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

#Knowledge：

1. 一开始考虑这个问题的时候，我在思考空间上考虑多一个列表保存元音，然后利用一个新的字典保存enumerate找到的原因，但是在互换位置的时候，我遇到了困惑。原来这是一道首尾双指针的问题。
2. 