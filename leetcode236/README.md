### 思路

对于二叉树的最近公共祖先来说分三种情况
1. 根节点的左右子树分别包含左右子树那么该节点就是最近公共祖先
2. 如果一个节点是另外一个节点的父节点，那么该节点就是最近共祖先
3. 如果根节点的左子树或者右子树同时包含两个节点的话那么对左子树或者右子树重复步骤1

### 代码
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {

    //判断是否一个节点包含另外一个节点
    public boolean containTreeNode( TreeNode root, TreeNode a){
        if (root == null || a == null){
            return false;
        }
        if(root.val == a.val){
            return true;
        }else {
            return containTreeNode(root.left,a) || containTreeNode(root.right,a) ;
        }
    }

    //主函数
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        if(this.containTreeNode(root.left,p) && this.containTreeNode(root.right,q) || this.containTreeNode(root.left,q) && this.containTreeNode(root.right,p)){
            return root;
        } else if(this.containTreeNode(root.right,p) && this.containTreeNode(root.right,q)){
            return lowestCommonAncestor(root.right,p,q);
        } else if(this.containTreeNode(root.left,p) && this.containTreeNode(root.left,q)){
            return lowestCommonAncestor(root.left,p,q);
        }else if(this.containTreeNode(p,q)){
            return p;
        }else if (this.containTreeNode(q,p)){
            return q;
        }else {
            return null;
        }
    }
}
```