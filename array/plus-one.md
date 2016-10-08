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

1. 这道题我一开始没有都明白题目，后来网上搜了后才知道题目的意思是将一个数字的每个位上的数字分别存到一个一维向量中，最高位在最开头，我们需要给这个数字加一，即在末尾数字加一，如果末尾数字是9，那么则会有进位问题，而如果前面位上的数字仍为9，则需要继续向前进位。**这说明经历的题目还是较少，因此不明白许多情况。**

2. **reversed()函数是返回序列的反向访问的迭代器**，注意返回的是迭代器，若要输出要么list化，要么for遍历迭代器。常用语法为：
   ```python
   print list(reversed(['dream','a','have','I']))
   #['I', 'have', 'a', 'dream']
   ```
3. 

