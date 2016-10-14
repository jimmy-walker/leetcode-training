#Question
**Given two sorted integer arrays nums1 and nums2, merge nums2 into nums1 as one sorted array.**

#Hint
You may assume that nums1 has enough space (size that is greater or equal to m + n) to hold additional elements from nums2. The number of elements initialized in nums1 and nums2 are m and n respectively.

#Answer
##solution1：I prefer this one, cause it use the python advantage.
```python
class Solution(object):
    def merge(self, nums1, m, nums2, n):
        """
        :type nums1: List[int]
        :type m: int
        :type nums2: List[int]
        :type n: int
        :rtype: void Do not return anything, modify nums1 in-place instead.
        """
        nums1[m:] = nums2[:n]
        nums1.sort()
```
##solution2: this is my answer. it has some problems.
```python
class Solution(object):
    def merge(self, nums1, m, nums2, n):
        """
        :type nums1: List[int]
        :type m: int
        :type nums2: List[int]
        :type n: int
        :rtype: void Do not return anything, modify nums1 in-place instead.
        """
        if n:
            if m:
                nums1 += nums2
            else:
                nums1 = nums2
            nums1.sort()
```

##solution3: 
```python
class Solution:
    # @param A  a list of integers
    # @param m  an integer, length of A
    # @param B  a list of integers
    # @param n  an integer, length of B
    # @return nothing
    def merge(self, A, m, B, n):
        last, i, j = m + n - 1, m - 1, n - 1
        
        while i >= 0 and j >= 0:
            if A[i] > B[j]:
                A[last] = A[i]
                last, i = last - 1, i - 1
            else:
                A[last] = B[j]
                last, j = last - 1, j - 1
        
        while j >= 0:
                A[last] = B[j]
                last, j = last - 1, j - 1
```

#Knowledge：
1. 这道第题目一开始我以为非常简单，因为我倾向于使用python的优点sort函数，而不是向解法三一样，完全靠算法。因为我认为正是这些既有的函数才使得python变得简单易用，我的目的也是使用python来解决各种问题。因此这里并没有对解法三进行研究。

2. 我本来使用等号直接复制，但是这里面就牵涉到python的原理，**python的赋值语句总是建立对象的引用值，而不是复制对象。因此，python 变量更像是指针，而不是数据存储区域**。
![](/assets/python copy.jpg)
**Python 没有「变量」，我们平时所说的变量其实只是「标签」，是引用**。

    看下面的例子，Python做的事情是首先创建一个列表对象 [0, 1, 2]，然后给它贴上名为 values 的标签。如果随后又执行values = [3, 4, 5]的话，Python 做的事情是创建另一个列表对象 [3, 4, 5]，然后**把刚才那张名为 values 的标签从前面的 [0, 1, 2] 对象上撕下来，重新贴到 [3, 4, 5] 这个对象上**。
    ```python
    values = [0, 1, 2]

    ```
    ```python
    values = [3, 4, 5]
    ```

3. 所以这道题目中我的解法nums1 = nums2，虽然使得nums的标签贴在了nums2的对象上（即取得了引用），但是nums1本身对应的对象始终没有改变。因而会报错。

4. **对于一个列表或者类似的序列或者其他复杂的对象，使用切片操作来取得拷贝，避免使用等号直接赋值**。

#Reference:
- [python基础（5）：深入理解 python 中的赋值、引用、拷贝、作用域](https://my.oschina.net/leejun2005/blog/145911)
- [Python关于对象的复制](http://www.jianshu.com/p/bc356a698af6)


