**Sum of Left Leaves🏍**<br><br>

Leet code link: https://leetcode.com/problems/sum-of-left-leaves/<br><br>

**Time Complexity of below solution**<br>
**O(n)**, we are visiting every node in the tree. <br><br>

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
    int sum = 0;
    public int sumOfLeftLeaves(TreeNode root) {
        inOrder(root, false);
        return sum;
    }
    
    void inOrder(TreeNode root, boolean fromLeft) {
        if(root == null)
            return;
        
        inOrder(root.left, true);
        if(root.left == null && root.right == null && fromLeft) 
            sum += root.val;
        inOrder(root.right, false);
    }
}
```
