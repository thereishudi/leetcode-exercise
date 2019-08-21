
### 思路

- 从根节点开始遍历树
- 如果节点 pp 和节点 qq 都在右子树上，那么以右孩子为根节点继续 1 的操作
- 如果节点 pp 和节点 qq 都在左子树上，那么以左孩子为根节点继续 1 的操作
- 如果条件 2 和条件 3 都不成立，这就意味着我们已经找到节 pp 和节点 qq 的 LCA 了


### 代码实现

```java


/**
 public class TreeNode {
 int val = 0;
 TreeNode left = null;
 TreeNode right = null;

 public TreeNode(int val) {
 this.val = val;

 }

 }
 */
public class Solution {
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        if (root == null || p == null || q == null){
            return null;
        }

        int max = p.val>q.val?p.val:q.val;
        int min = p.val<q.val?p.val:q.val;
        if(root.val>min && root.val<max ){
            return root;
        }
        if (root.val>max){
            return lowestCommonAncestor(root.left,p,q);
        }
        if (root.val<min) {
            return lowestCommonAncestor(root.right, p, q);
        }else {
            return root;
        }
    }
}
```