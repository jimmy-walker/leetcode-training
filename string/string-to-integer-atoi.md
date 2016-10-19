#Question
**Implement `atoi` to convert a string to an integer.**


#Hint
Carefully consider all possible input cases. If you want a challenge, please do not see below and ask yourself what are the possible input cases.

It is intended for this problem to be specified vaguely (ie, no given input specs). You are responsible to gather all the input requirements up front.

The function first discards as many whitespace characters as necessary until the first non-whitespace character is found. Then, starting from this character, takes an optional initial plus or minus sign followed by as many numerical digits as possible, and interprets them as a numerical value.

The string can contain additional characters after those that form the integral number, which are ignored and have no effect on the behavior of this function.

If the first sequence of non-whitespace characters in str is not a valid integral number, or if no such sequence exists because either str is empty or it contains only whitespace characters, no conversion is performed.

If no valid conversion could be performed, a zero value is returned. If the correct value is out of the range of representable values, INT_MAX (2147483647) or INT_MIN (-2147483648) is returned.

#Answer
## solution：
```python
class Solution(object):
    def myAtoi(self, str):
        """
        :type str: str
        :rtype: int
        """
        str = str.strip()
        if str == "" :
            return 0
        i = 0
        sign = 1
        ret = 0
        length = len(str)
        MaxInt = (1 << 31) - 1
        if str[i] == '+':
            i += 1
        elif str[i] == '-' :
            i += 1
            sign = -1
        
        for i in range(i, length) :
            if str[i] < '0' or str[i] > '9' :
                break
            ret = ret * 10 + int(str[i])
            if ret > sys.maxint:
                break
        ret *= sign
        if ret >= MaxInt:
            return MaxInt
        if ret < MaxInt * -1 :
            return MaxInt * - 1 - 1 
        return ret   
```

#Knowledge：
1. 这道题目预想到了思考部分的空间（原位操作）及时间（单指针），但是在编程环节，没想出怎么叠加数字以及遇到任何怪字符就跳开的方法，方法为**循环跳出：在for循环中加入break，一旦遇到不符合条件的就结束循环**：

    ```python
    for i in range(i, length):
        if str[i] < '0' or str[i] > '9':                        
            break
    ```

2. python中去除string中空格的方法