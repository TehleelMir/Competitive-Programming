**Validate Binary Search Tree🚂**<br><br>

Leet code link: https://leetcode.com/problems/validate-binary-search-tree/ <br><br>

**Time complexity of below solution**<br>
**O(n)** sence we are visting each nodes only once.<br><br>

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
    Integer previous    = null;
    boolean result      = true;
    
    public boolean isValidBST(TreeNode root) {
       inOrderTraversal(root);
       return result;
    }
    
    void inOrderTraversal(TreeNode root) {
        if(root == null) return;
        
        inOrderTraversal(root.left);
        
        if(previous != null && previous >= root.val) {
            result = false;
            return;
        }
        previous = root.val;
        
        inOrderTraversal(root.right);
    }
}
```
