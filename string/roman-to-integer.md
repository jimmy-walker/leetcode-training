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
        pre = sum = 0
        for i in s: 
            if pre < romans[i]:
                sum += -2 * pre + romans[i]
            else:
                sum += romans[i]
            pre = romans[i]
        return sum   
```
#Knowledge：
1. 这道题目主要是背景知识不明确，因而没有解答出：

    1. 罗马数字有如下符号：`Ⅰ（1）Ⅴ（5）Ⅹ（10）L（50）C（100）D（500）M（1000）`

    2. 小数字在大数字前面表示的数是用大数字减去小数字，如IV＝4

    3. 小数字在大数字后面表示的数是用大数字加上小数字，如VI=6

2. 定下方案，在思考空间上是原位操作，增加一个sum值记录结果，而在时间上则是单指针从前往后。在编程的时候，则是加上了一个pre值记录前一个数字。总体思路为：从前往后遍历罗马数字，如果某个数比前一个数小，则把该数加入到结果中；反之，则在结果中两次减去前一个数并加上当前这个数。