## 二叉树的递归与非递归先序遍历

- 先序遍历 中左右

```java
public class Traveral {

    /**
     * 递归ban
     */
    //先序遍历
    public static List<Integer> preOrder (TreeNode node) {
        List<Integer> ans = new ArrayList<>();
        if (node == null) {
            return ans;
        }
        ans.add(node.val);
        preOrder(node.left);
        preOrder(node.right);
        return ans;
    }


    /**
     * 非递归版本
     */
    //先序遍历
    public static List<Integer> preOrderWithStack (TreeNode node) {
        List<Integer> ans = new ArrayList<>();
        if (node == null) {
            return ans;
        }
        Stack<TreeNode> stack = new Stack<>();
        TreeNode cur;
        stack.push(node);
        while (!stack.isEmpty()) {
            cur = stack.pop();
            if (cur!=null) {
                ans.add(cur.val);
                stack.push(node.left);
                stack.push(node.right);
            }
        }
        return ans;
    }

}
```

