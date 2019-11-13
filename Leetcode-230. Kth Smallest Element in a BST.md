## 中序遍历题目

inorder类型

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
    int count;
    int res;
    
    public int kthSmallest(TreeNode root, int k) {
        count = k;
        res = 0;
        helper(root);
        return res;
    }
    
    public void helper(TreeNode root) {
        if (root == null) return;
        helper(root.left);
        count--;
        if (count == 0) {
            res = root.val;
        }
        helper(root.right);
    }
}
```