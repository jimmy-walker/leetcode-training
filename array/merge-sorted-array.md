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

2. 我本来使用等号直接复制


#Reference:



