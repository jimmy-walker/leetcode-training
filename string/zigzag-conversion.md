#Question

**The string `"PAYPALISHIRING"` is written in a zigzag pattern on a given number of rows like this: (you may want to display this pattern in a fixed font for better legibility)**
```
P   A   H   N
A P L S I I G
Y   I   R
```
And then read line by line: "PAHNAPLSIIGYIR"
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
        strings = [""] * numRows
        # go through the string and append letters one by one
        lpos = 0
        for letter in s:
            strings[lpos] += letter
            if lpos == numRows - 1:
                lpos -= 1
                down = False
            elif lpos == 0:
                lpos = 1
                down = True
            elif down:
                lpos += 1
            else:
                lpos -= 1
        return "".join(strings)
```
#Knowledge：
1. 