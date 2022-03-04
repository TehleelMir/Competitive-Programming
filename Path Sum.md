**Path Sum🚚**<br><br>

Leet code link: https://leetcode.com/problems/path-sum/ <br><br>

**Time Complexity of below solution**<br><br>
**O(n)**, we are simply doing a pre-order traversal on the tree which takes n time. <br>


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
    boolean flag = false;
    int sumTill = 0;
    public boolean hasPathSum(TreeNode root, int sum) {
        preOrder(root, sum);
        return flag;
    }
    
    void preOrder(TreeNode root, int sum) {
        if(root == null) return;
        sumTill += root.val;
        
        if(root.left == null && root.right == null && sumTill == sum) {
            flag = true; 
            return; 
        }
        
        preOrder(root.left, sum);
        preOrder(root.right, sum);
        sumTill -= root.val;
    }
}
```
