#Question
**Given a string s consists of upper/lower-case alphabets and empty space characters `' '`, return the length of last word in the string.
**
If the last word does not exist, return 0.
#Example:
Given s = `"Hello World"`,

return `5`. 
#Answer
##solution：this is done myself
```python
class Solution(object):
    def lengthOfLastWord(self, s):
        """
        :type s: str
        :rtype: int
        """
        a = re.findall("[A-Za-z]+",s)
        if a:
            return len(a[-1])
        else:
            return 0
```
#Knowledge：
1. 这道题目并不难，因为有python的特性。