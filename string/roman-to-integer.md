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
