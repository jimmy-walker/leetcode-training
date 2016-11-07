# Question

**Given a binary tree, return the level order traversal of its nodes' values. \(ie, from left to right, level by level\).**

# Example:

Given binary tree `[3,9,20,null,null,15,7]`,

```
    3
   / \
  9  20
    /  \
   15   7
```

return its level order traversal as:

```
[
  [3],
  [9,20],
  [15,7]
]
```

# Answer

## solution：

```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def levelOrder(self, root):
        """
        :type root: TreeNode
        :rtype: List[List[int]]
        """
        if not root:
            return []
        ans, level = [], [root]
        while level:
            ans.append([node.val for node in level])
            temp = []
            for node in level:
                temp.extend([node.left, node.right])
            level = [leaf for leaf in temp if leaf]
        return ans     
```

# Knowledge：

1. 这道题一开始我没看明白。一直在思考怎么用python来表达tree。后来看了网上文章后才明白，预先已经定义TreeNode了。因此在本地调试时，就需要先定义这个类才行。而在使用时，**访问树问题：实际上root代表了一个树结点！通过其left和right才能遍历往下，不断切换新的结点，这是树的特点！！！**
  ```python
   root = TreeNode(1)
   root.left = TreeNode(1.5)
   root.right = TreeNode(2)
   root.right.left = TreeNode(3)
   result = Solution().preorderTraversal(root)
  ```

2. 以下是一些调试信息，帮助理解上面代码。**遍历树问题：遍历列表中结点的值（val）保存，再将非None的子结点生成一个list赋给level** = `[leaf for leaf in temp if leaf]`，**从而不断寻找一直到None，跳出**`while leaf`。

  ```
   ans
   [[1]]
   temp
   [<__main__.TreeNode object at 0x0000000003ED4DA0>, <__main__.TreeNode object at 0x0000000003ED4A58>]
   ans
   [[1], [1.5, 2]]
   temp
   [None, None]
   temp
   [None, None, <__main__.TreeNode object at 0x0000000003ED4B00>, None]
   ans
   [[1], [1.5, 2], [3]]
   temp
   [None, None]
  ```

3. 具体代码编写中，可以这么思考：

  ```
    对于树结点，ans.append(root.val)
        
  ```


