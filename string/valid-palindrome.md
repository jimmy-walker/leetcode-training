#Question
**Given a string, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.** 

#Example:
`"A man, a plan, a canal: Panama"` is a palindrome.


`"race a car"` is not a palindrome.

#Hint
Have you consider that the string might be empty? This is a good question to ask during an interview.

For the purpose of this problem, we define empty string as valid palindrome.

#Answer
##solution：
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