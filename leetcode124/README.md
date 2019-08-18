### 思路
这道题是一个获取最大路径的题目

		
只要递归的去找到一个节点的左边最大值和右边最大值然后和中间节点的最大值进行比较就可以了

### 代码实现

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
    //设置全局变量
    int max_sum = Integer.MIN_VALUE;

    public int max_gain(TreeNode node) {
        if (node == null) return 0;
        
        int left = Math.max(max_gain(node.left), 0);
        int right = Math.max(max_gain(node.right), 0);


        int sum = node.val + left + right;


        max_sum = Math.max(max_sum, sum);

        return node.val + Math.max(left, right);
  }

  public int maxPathSum(TreeNode root) {
    max_gain(root);
    return max_sum;
  }
}
```