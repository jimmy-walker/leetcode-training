#Question
**Given two binary trees, write a function to check if they are equal or not.**

Two binary trees are considered equal if they are structurally identical and the nodes have the same value.

#Answer
##solution：
```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def isSameTree(self, p, q):
        """
        :type p: TreeNode
        :type q: TreeNode
        :rtype: bool
        """
        if p is None and q is None:
            return True
        
        if p is not None and q is not None:
            return p.val == q.val and self.isSameTree(p.left, q.left) and self.isSameTree(p.right, q.right)
        
        return False
```

#Knowledge：
1. 这道题目是**遍历树问题——按路径遍历（迭代）**的一个变种，还是使用迭代技术。

2. 在思考时间和空间时，关键是注意以下几点，才能抽象出编程中的迭代：**要从头开始将每一个结果每一个步骤都写出来；找到过程中循环的部分，将其进行递归化，其中多个if部分，可以写成并集（and）**。

```


```