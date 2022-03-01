**Minimum Depth of Binary Tree🛩**<br><br>

Leet code link: https://leetcode.com/problems/minimum-depth-of-binary-tree/ <br><br>

Two different solutions with same time complexity but one is using Breadth-first search technique to traverse the tree level by level and the other one is using pre-order traverse
i.e. node->left->right<br><br>

**Time Complexity of below solutions**<br>
**O(n)**, in the pre-order traversal we are visiting each node only once and in the case of breadth-first search it may seem first its not O(n) because of the inner loop but it is
O(n). <br>
Here is the explanation, the outer loop will run O(log n) i.e. the number of levels a tree has and the inner loop will run O(n), and since as it's the rule of big O to drop
non dominate terms that's why O(n). <br>
In reality, Breadth-first search is more efficient than the first one since its checks the tree level by level and as soon as it detects the node with no childrens it stops the 
execution. 

<br><br>
**Code**<br><br>
**Pre-Order**<br>
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
    int min = -1;
    int count = 0;
    public int minDepth(TreeNode root) {
        if(root == null) return 0;
        preOrder(root);
        return min;
    }
    
    void preOrder(TreeNode root) {
        if(root == null || (min != -1 && count+1 > min)) return;
        
        count++;
        
        if(root.left == null && root.right == null) 
            min = (min == -1)? count : Math.min(min, count);
        preOrder(root.left);
        preOrder(root.right);
        
        count--;
    }
}
```
<br><br>
**BTF**<br>
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
    public int minDepth(TreeNode root) {
        if(root == null)    return 0;
        return              levelOrder(root);
    }
    
    int levelOrder(TreeNode root) {
        Queue<TreeNode> queue = new LinkedList<TreeNode>();
        queue.offer(root);
        int depth = 1;
        
        while(!queue.isEmpty()) {
          int size = queue.size();
            
            for(int i=0; i<size; i++) {
                TreeNode temp =  queue.poll();
                if(temp.left  == null && temp.right == null)    return depth;
                if(temp.left  != null)                          queue.offer(temp.left);
                if(temp.right != null)                          queue.offer(temp.right);
            }
            depth++;
        }
        return depth;
    }
}
```
