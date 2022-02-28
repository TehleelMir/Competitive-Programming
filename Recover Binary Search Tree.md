**Recover Binary Search Tree🦽**<br><br>

Leet code link: https://leetcode.com/problems/recover-binary-search-tree/ <br><br>

**Time Complexity**<br>
**O(n)**, we are doing an inorder traversal of the tree and that takes O(n) time. 
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
    TreeNode firstElement = null;
    TreeNode secondElement = null;
    TreeNode prevNode = new TreeNode(Integer.MIN_VALUE);
    public void recoverTree(TreeNode root) {
        inOrder(root);
        int temp = firstElement.val;
        firstElement.val = secondElement.val;
        secondElement.val = temp;
    }
    
    void inOrder(TreeNode root){
        if(root == null) return;
        
        inOrder(root.left);
        
        if(firstElement == null && prevNode.val > root.val) firstElement = prevNode;
        if(firstElement != null && prevNode.val > root.val) secondElement = root;
        prevNode = root;
        
        inOrder(root.right);
    }
}
```
