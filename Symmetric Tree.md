**Symmetric Tree🏢**<br><br>

Leet code link: https://leetcode.com/problems/symmetric-tree/ <br><br>

**Time Complexity of below solution**<br>
**O(n/2)**, Because on each level of recursion we check/visiting two nodes at a time. 

<br><br>
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
    public boolean isSymmetric(TreeNode root) {
        return root==null || isMirror(root.left, root.right);
    }
    
    boolean isMirror(TreeNode left, TreeNode right) {
        if(left == null || right == null) 
            return left == right;
        
        if(left.val != right.val) 
            return false;
        
        return isMirror(left.left , right.right) && isMirror(left.right , right.left);
    }
}
```
