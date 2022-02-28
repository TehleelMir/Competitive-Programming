**Binary Tree Inorder Traversal🛹**<br><br>

Leet code link: https://leetcode.com/problems/binary-tree-inorder-traversal/ <br><br>

**Time Complexity**<br>
**O(n)** both for space and time
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
    LinkedList<Integer> list = new LinkedList<>();
    public List<Integer> inorderTraversal(TreeNode root) {
        inOrderTraversal(root);
        return list;
    }
    
    void inOrderTraversal(TreeNode root) {
        if(root == null) return;
        inOrderTraversal(root.left);
        list.add(root.val);
        inOrderTraversal(root.right);
    }
}
```
