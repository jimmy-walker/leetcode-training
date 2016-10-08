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
        carry = 1 #进位
        for i in reversed(xrange(len(digits))): #从低位到高位计算，任何一位都加上进位，进位可能为1也可能为0。
            digits[i] += carry #每位都要加上前面的进位，然后除以10，余数就是当前位的结果，商就是进位。
            carry = digits[i] / 10
            digits[i] %= 10
        
        if carry: #只有当一直算到最后，算到最高位进位还是1的时候，因为最高位需要进位，原来的数组一定是N个9，现在变成N个0，所以这时只要将最高位置为1，直接加上现在的N个0即可。
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

3. 考察基本的按位加法和进位。注意：从低位到高位计算，每位都要加上前面的进位，然后除以10，余数就是当前位的结果，商就是进位。

4. **余数为`A%10`; 商为`A/10`**。

