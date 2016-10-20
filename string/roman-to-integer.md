#Question
**Given a roman numeral, convert it to an integer.**

Input is guaranteed to be within the range from 1 to 3999. 

#Answer
##solution：
```python
class Solution(object):
    def romanToInt(self, s):
        """
        :type s: str
        :rtype: int
        """
        romans = {'M': 1000, 'D': 500 , 'C': 100, 'L': 50, 'X': 10,'V': 5,'I': 1}
        prev_value = running_total =0        
        for i in range(len(s)-1, -1, -1):
            int_val = romans[s[i]]
            if int_val < prev_value:
                running_total -= int_val
            else:
                running_total += int_val
            prev_value = int_val
        return running_total 
```
#Knowledge：
1. 这道题目主要是背景知识不明确，因而没有解答出：

    1. 罗马数字有如下符号：`Ⅰ（1）Ⅴ（5）Ⅹ（10）L（50）C（100）D（500）M（1000）`

    2. 小数字在大数字前面表示的数是用大数字减去小数字，如IV＝4

    3. 小数字在大数字后面表示的数是用大数字加上小数字，如VI=6

2. 