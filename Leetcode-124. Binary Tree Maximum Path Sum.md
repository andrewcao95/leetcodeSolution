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
    int res;
    
    public int maxPathSum(TreeNode root) {
        if (root == null) return 0;
        res = Integer.MIN_VALUE;
        helper(root);
        return res;
    }
    
    public int helper(TreeNode root) {
        if (root == null) return 0;
        int left = Math.max(0, helper(root.left));//当遇到负值的时候，直接取正值
        int right = Math.max(0, helper(root.right));
        res = Math.max(res, left + right + root.val); //注意这里，return返回的是一条分支上的最大值
        return Math.max(left, right) + root.val; //而res返回的是分支的最大值
    }
}
```