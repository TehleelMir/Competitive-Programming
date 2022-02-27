**Representation of binary tree in an array🛁**<br><br>

**Time Complexity**<br>
**O(n)** where n is the number of nodes tree have, because we are visiting each node only one time. 
<br><br>

**Code**<br>
```
public class ArrayRepresentationOfBinaryTree {
    public static void main(String[] args) {
        Node a = new Node(50);
        Node b = new Node(30);
        Node c = new Node(20);
        Node d = new Node(15);
        Node e = new Node(10);
        Node f = new Node(8);
        Node g = new Node(16);
        a.left = b;
        a.right = c;
        b.left = d;
        b.right = e;
        c.left = f;
        c.right = g;
        /*
        so here we have a binary tree, with the root a.
        Now we have to represent this binary tree in an array.
        The array will store the binary tree nodes in level wise order, And
        if a index is at i
        its left child will be at 2*i (in the array)
        its right child will be at 2*i+1
        and its parent is going to be at i/2
        */
        ArrayList<Node> arr = storeTheTreeInAnArrayLevelWise(a);
        for(int i=1; i<=arr.size(); i++) {
            int indexOfParent = i/2;
            int indexOfLeft = 2*i;
            int indexOfRight = (2*i) + 1;
            System.out.println("node "+arr.get(i-1).val);
            if(indexOfParent > 0)
                System.out.println("parent " +arr.get(indexOfParent-1).val);
            if(indexOfLeft < arr.size())
                System.out.println("left "+arr.get(indexOfLeft-1).val);
            if(indexOfRight < arr.size())
                System.out.println("right "+arr.get(indexOfRight-1).val);
            System.out.println("");
        }
    }

    static ArrayList<Node> storeTheTreeInAnArrayLevelWise(Node root) {
        ArrayList<Node> list = new ArrayList<>();
        LinkedList<Node> queue = new LinkedList<>();
        queue.add(root);
        while(!queue.isEmpty()) {
            Node temp = queue.remove();
            if(temp.left != null) queue.add(temp.left);
            if(temp.right != null) queue.add(temp.right);
            list.add(temp);
        }
        return list;
    }
}

class Node {
    int val;
    Node left, right;
    Node(int val) {
        this.val = val;
    }
}
```
