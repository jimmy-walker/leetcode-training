#Question
**Given a non-negative number represented as an array of digits, plus one to the number.**

The digits are stored such that the most significant digit is at the head of the list.

#Answer
## solution：

```python
class Solution(object):
    def plusOne(self, digits):
        """
        :type digits: List[int]
        :rtype: List[int]
        """
        carry = 1
        for i in reversed(xrange(len(digits))):
            digits[i] += carry
            carry = digits[i] / 10
            digits[i] %= 10
        
        if carry:
            digits = [1] + digits
        
        return digits   
```

#Knowledge：

1. 


