### 思路
这道题可以先用数组按照中序遍历的方式存储节点，然后获得倒数第k个节点，但是这种方法的时间复杂度很高

第二种就是利用中序遍历的递归到倒数第k个节点。
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
    int count = 0;
    public int dfs(TreeNode root){
        if(root == null){
            return -1;
        }
        if(count == 0){
            return root.val;
        }
        dfs(root.left);
        count --;
        if(count == 0){
            return root.val;
        }
        dfs(root.right);
        return root.val;
    }
    public int kthSmallest(TreeNode root, int k) {
        count = k;
        dfs(root);
        return dfs(root);
    }
}
```