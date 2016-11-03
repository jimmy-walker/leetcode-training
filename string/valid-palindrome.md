#Question
**Given a string, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.** 

#Example:
`"A man, a plan, a canal: Panama"` is a palindrome.


`"race a car"` is not a palindrome.

#Hint
Have you consider that the string might be empty? This is a good question to ask during an interview.

For the purpose of this problem, we define empty string as valid palindrome.

#Answer
##solution：this is done myself.
```python
class Solution(object):
    def isPalindrome(self, s):
        """
        :type s: str
        :rtype: bool
        """
        a = []
        for i in s:
            [a.append(b) for b in re.findall("[A-Za-z0-9]+",i) if b]
            
        for i in xrange((len(a))/2):
            if a[i].lower() == a[len(a)-1-i].lower():
                pass
            else:
                return False
        return True
```

#Knowledge：
1. 这道题一开始没弄懂什么是palindrome，后来查了下才知道，原来是首末逐一相等。于是简单思考了下，就定下了做法。现在思考过程中由于已经有意识到把字符串进行遍历循环寻找等按存储来思考，所以有时候自己不是很讲究空间或是时间的划分。

2. 具体在解决过程中，主要难点是正则表达式re.findall，其语法如下：

```python
re.findall(pattern, string[, flags]):#搜索string，以列表形式返回全部能匹配的子串。
```