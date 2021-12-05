## Construct-binary-tree-from-inorder-and-postorder-traversal



#### Description

根据一棵树的中序遍历与后序遍历构造二叉树。

**注意:**
你可以假设树中没有重复的元素。



#### Example

**example 1:**

```
中序遍历 inorder = [9,3,15,20,7]
后序遍历 postorder = [9,15,7,20,3]
```

返回如下的二叉树：

```
    3
   / \
  9  20
    /  \
   15   7
```



#### Solution

```js
var buildTree = function(inorder, postorder) {
    if (!postorder.length) return null
    
    let root = new TreeNode(postorder[postorder.length - 1])    
    let index = inorder.findIndex(number => number === root.val)
    
    root.left = buildTree(inorder.slice(0, index), postorder.slice(0, index))
    root.right = buildTree(inorder.slice(index + 1, inorder.length), postorder.slice(index, postorder.length - 1))
    
    return root
};
```



#### Result

![image-20211205223941796](image/image-20211205223941796.png)