#### [236. 二叉树的最近公共祖先](https://leetcode-cn.com/problems/lowest-common-ancestor-of-a-binary-tree/)

![image-20220507211508361](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20220507211508361.png)



```java
class Solution {
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        if(root == null){
            return null;
        }
        if(root == p || root == q){
            return root;
        }

        TreeNode left = lowestCommonAncestor(root.left,p,q);
        TreeNode right = lowestCommonAncestor(root.right,p,q);
        if(left != null && right != null){
            return root;
        }else if(left == null){
            return right;
        }else if(right == null){
            return left;
        }else{
            return null;
        }
    }
}
```

**注意点：**

**也是想明白递归的每一步在干什么，这道题目其实运用了分类讨论的思想。**

**1.如果p,q分布在根节点的两侧，那么最近公共祖先就是最近根节点**

**2.如果分布在一侧，那么就是一侧根节点left or right.**