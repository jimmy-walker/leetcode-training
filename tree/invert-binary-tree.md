#Question
**Invert a binary tree. **

#Example:
```
     4
   /   \
  2     7
 / \   / \
1   3 6   9
```

```
     4
   /   \
  7     2
 / \   / \
9   6 3   1
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
    def invertTree(self, root):
        """
        :type root: TreeNode
        :rtype: TreeNode
        """
        if root is not None:
            root.left, root.right = self.invertTree(root.right),self.invertTree(root.left)
        return root
```

#Knowledge：
1. 这道题目出现在了数据挖掘的面试题里面，因此值得重视。

2. 这道题目一开始就知道是递归，但是在思考和编程过程的时候遇到点小问题，就是**递归程序写法**：1.先写出整个具体操作过程以及用等号划出需要递归的部分。2.确定函数return的返回形式。3.递归位置的形式一定是"参数=函数"的形式：**4.可能之前一些位置的语句也要被递归形式代替"参数=函数"**。

    ```python
    if root is not None:
        root.left, root.right = root.right,root,left #若非None，则引用left，right不会出错，直接互换其左右节点
        ======分别判断左右结点是不是None，再将它们各自的左右结点互换，由此发现可以递归======
    return root #如果root就是None的话，直接返回本身，因为不需要翻转了
    ```

    ```python
    if root is not None:
        root.left, root.right = self.invertTree(root.right),self.invertTree(root.left) #发现需要递归的形式，与上一句语句类似，因此决定将其代替。
    return root #如果root就是None的话，直接返回本身，因为不需要翻转了
    ```
