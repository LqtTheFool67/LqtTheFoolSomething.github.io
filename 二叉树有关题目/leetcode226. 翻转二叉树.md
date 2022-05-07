#### [226. 翻转二叉树](https://leetcode-cn.com/problems/invert-binary-tree/)![image-20220507212633458](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20220507212633458.png)



```java
class Solution {
    public TreeNode invertTree(TreeNode root) {
        if(root == null)return null;

        TreeNode left = invertTree(root.left);
        TreeNode right = invertTree(root.right);
        root.left = right;
        root.right = left;
        return root;
    }
}
```

