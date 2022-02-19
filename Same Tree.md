**Same Tree🎹**<br>

Leet code link: https://leetcode.com/problems/same-tree/ <br><br>

**O(n)** <br>
Where n is the number of nodes in a tree<br>
Ps: in case of java the n will be the number of nodes in a tree, but the tree which have less number of nodes in it. Because Java does have short circuit evaluation.
<br>
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
    public boolean isSameTree(TreeNode p, TreeNode q) {
        if(p == null && q == null) 
            return true;
        if(p == null || q == null)
            return false;
        if(p.val != q.val)
            return false;
        return (isSameTree(p.left, q.left) && isSameTree(p.right, q.right));
    }
}
```
