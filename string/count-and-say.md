#Question
The count-and-say sequence is the sequence of integers beginning as follows:

`1, 11, 21, 1211, 111221, ...`

`1` is read off as `"one 1"` or `11`.


`11` is read off as `"two 1s"` or `21`.

`21` is read off as `"one 2, then one 1"` or `1211`.

Given an integer n, generate the $$n^{th}$$ sequence.

#Answer
##solution：
```python
class Solution(object):
    def countAndSay(self, n):
        """
        :type n: int
        :rtype: str
        """
        s = '1'
        for _ in xrange(n - 1):
            s = re.sub(r'(.)\1*', lambda m: str(len(m.group(0))) + m.group(1), s)
        return s
```
#Knowledge：
1. 这道题目一开始就没理解到题意，后来才知道，是生成一种特定的序列，输入n，则返回该序列第n个的值。

2. 这种产生**固定序列类的题，预设初始值s，然后根据修改再返回新s**。

3. **正则表达式**的使用

    1.** re.sub有三个必选参数：pattern（正则表达式）, repl（replace替换值）, string（原字符串），返回替换后的字符串**：

    ```
    re.sub(pattern, repl, string)
    ```

    2. 