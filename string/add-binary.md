#Question
**Given two binary strings, return their sum (also a binary string).**

#Example
For example,
a = `"11"`
b = `"1"`
Return `"100"`.

#Answer
##solution：
```python
class Solution(object):
    def addBinary(self, a, b):
        """
        :type a: str
        :type b: str
        :rtype: str
        """
        return bin(int(a,2)+int(b,2))[2:]
```

#Knowledge：

1. 这道题目我投机取巧了一把，使用了高级语言python，就不用按位操作了...我一直认为要发挥高级语言的优势嘛...

2. python中的进制转换，**十进制是int类型，而另一种进制是字符串，往往有"0b"等标识符，可以用[2:]去除**。

    1. 二进制转十进制：**int(x, base=2)** #if base is given, then x must be a string

    ```python
    int('100',2) #结果为4
    ```
    2. 十进制转二进制：**bin(number)** #Return the binary representation of an integer

    ```python
    bin(4) #结果为"ob100"
    ```


