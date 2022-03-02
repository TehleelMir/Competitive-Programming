**Binary Tree Level Order Traversal🚄**<br><br>

Leet code link: https://leetcode.com/problems/binary-tree-level-order-traversal/ <br><br>

**Time complexity of below solution**<br>
**O(n)** the inner loop will go through the every node of the tree and the outer loop will run for each level i.e O(log n). Ignoring the outer loop we get O(n) as the 
main time complexity of this code.
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
    public List<List<Integer>> levelOrder(TreeNode root) {
        List<List<Integer>> list = new LinkedList<>();
        Queue<TreeNode> q = new LinkedList<>();
        
        if(root == null) return list;
        q.offer(root);
        
        while(!q.isEmpty()) {
            int size = q.size();
            List<Integer> tempList = new LinkedList<>();
             
            for(int i=0; i<size; i++) {
                TreeNode temp = q.poll();
                tempList.add(temp.val);
                if(temp.left  != null)  q.offer(temp.left);
                if(temp.right != null) q.offer(temp.right);
            }
            list.add(tempList);
        }
        
        return list;
    }
}
```
