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
1. 这道题一开始的时候，我试着按照思考的过程将程序写出来，用以提炼递归式。在写出了主框架后，遇到个问题就是感觉一开始root为空时返回的是true，但是后面的节点需要返回树的深度。于是看了下答案，发现其很巧妙地返回了两个值，然后再定义一个函数，专门取返回值的第二个值作为最后结果。
```python
if root is None:
    return True #如果root是None，那么就说明此root不违反平衡树
if root.left is not None or root.right is not None:
    ========判断此两个结点==========
return True #如果root.left，root.right都是None，那么就说明此root结点下的树是平衡树
```

```python
if root is None:
    return 0,True #增加一个返回（该结点下的深度）
if root.left is not None or root.right is not None:
    ========判断此两个结点==========

return 1,True#如果存在root，即使root.left，root.right都是None，那么root的深度也是

```
