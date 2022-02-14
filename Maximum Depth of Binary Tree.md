**Maximum Depth of Binary Tree🔭**<br>

Leet code link: https://leetcode.com/problems/maximum-depth-of-binary-tree/ <br><br>

**Time Complexity**<br>
The time complexity of the below solution is O(n) which is linear time. Because we are visiting each node only once, using the post traversal method (left -> right -> node).

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
    public int maxDepth(TreeNode root) {
        return postTraversal(root);
    }
    
    public int postTraversal(TreeNode root) {
        if(root == null) return 0;
        int l = postTraversal(root.left);
        int r = postTraversal(root.right);
        if(l > r) return l+1;
        else return r+1;
    }
}
```
