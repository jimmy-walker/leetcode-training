#Question

**The string `"PAYPALISHIRING"` is written in a zigzag pattern on a given number of rows like this: (you may want to display this pattern in a fixed font for better legibility)**
```
P   A   H   N
A P L S I I G
Y   I   R
```
And then read line by line: `"PAHNAPLSIIGYIR"`

Write the code that will take a string and make this conversion given a number of rows:
```
string convert(string text, int nRows);
```
`convert("PAYPALISHIRING", 3)` should return `"PAHNAPLSIIGYIR"`.
#Answer
## solution：
```python
class Solution(object):
    def convert(self, s, numRows):
        """
        :type s: str
        :type numRows: int
        :rtype: str
        """
        if numRows == 1:
            return s
        down = True
        strings = ['' for i in range(numRows)] #产生二维数组
        # go through the string and append letters one by one
        lpos = 0
        for letter in s:
            strings[lpos] += letter
            if lpos == numRows - 1:
                lpos -= 1
                down = False #如果到达最后一行，则停止下降
            elif lpos == 0:
                lpos = 1
                down = True #如果到达第一行，则停止上升
            elif down:
                lpos += 1
            else:
                lpos -= 1
        return "".join(strings)
```
#Knowledge：
1. 此题的典型的方法有两个：第一，用一个二维数组来存放，按照ZigZag的方式一列一列填充数组。然后按行访问就是新数组；第二，不使用额外空间，直接找出每一行不同字母在原字符串中的序号。我选择第一个，因为相对来说比较直观。

2. 产生二维数组来存放字符串的方法为：['' for i in range(numRows)]

3. 列表转字符串的方法：
    ```python
    "".join(A)
    ```