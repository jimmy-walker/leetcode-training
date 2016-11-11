#Question
**Given a binary tree, determine if it is height-balanced.**

For this problem, a height-balanced binary tree is defined as a binary tree in which the depth of the two subtrees of every node never differ by more than 1.

#Answer
##solution：this is partly done by myself
```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def isBalanced(self, root):
        """
        :type root: TreeNode
        :rtype: bool
        """
        return self.depthAndBalan(root)[1]        
        
    def depthAndBalan(self, root):
        if root is None:
            return 0, True
        if root.left is not None or root.right is not None:
            leftDep, leftBal = self.depthAndBalan(root.left)
            rightDep, rightBal = self.depthAndBalan(root.right)
            curBal = abs(leftDep - rightDep) <= 1
            return max(leftDep, rightDep)+1, leftBal and rightBal and curBal
        return 1, True
```

#Knowledge：
1. 