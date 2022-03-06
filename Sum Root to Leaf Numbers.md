**Sum Root to Leaf Numbers🚓**<br><br>

Leet code link: https://leetcode.com/problems/sum-root-to-leaf-numbers/ <br><br>

**Time Complexity of below solution**<br>
**O(n)**, we are visiting each node of the tree. 

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
    int sum = 0;
    int num = 0;
    public int sumNumbers(TreeNode root) {
        preOder(root);
        return sum;
    }
    
    void preOder(TreeNode root) {
        if(root == null)    return;
        
        num = num * 10 + root.val;
        if(root.left == null && root.right == null)
            sum += num;
            
        preOder(root.left);
        preOder(root.right);
        num /=10;
    }
}
```
