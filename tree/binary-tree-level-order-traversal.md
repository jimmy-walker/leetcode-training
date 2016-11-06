#Question
**Given a binary tree, return the level order traversal of its nodes' values. (ie, from left to right, level by level).**

#Example:
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

#Knowledge：
1. 这道题一开始我没看明白。一直在思考怎么用python来表达tree。后来看了网上文章后才明白，预先已经定义TreeNode了。而具体的