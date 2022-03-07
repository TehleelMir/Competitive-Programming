**Binary Tree Maximum Path Sum🧭**<br><br>

Leet Code Link: https://leetcode.com/problems/binary-tree-maximum-path-sum/ <br><br>

Time complexity of below solution<br>
**O(n)**, since its a simple pre-order traversal of a tree it will take n time. <br><br>

**Code**<br>
```
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    int sum = Integer.MIN_VALUE;
    public int maxPathSum(TreeNode root) {
        postOrder(root);
        return sum;
    }
    
    int postOrder(TreeNode root) {
        if(root == null) 
            return 0;
        int left  = postOrder(root.left);
        int right = postOrder(root.right);
        sum =  Math.max(sum, root.val + left + right);
        return Math.max(0, root.val + Math.max(left, right));
    }
}
```
