**Breadth-First Search🛒**<br>
Breadth-first search is a graph algorithm used to (find the shortest path between two nodes) (to check if there is a path between two nodes) and (also to 
simply traverse the graphic).<br>

In the below code im checking if there exists a path between two nodes. <br><br>

**Time Complixity**<br>
///
<br><br>

**Explanation*<br>
////
<br><br>

**Code**<br>
```
import java.util.ArrayList;
import java.util.HashSet;
import java.util.LinkedList;

import com.company.breadthFirstSearch.Node;

public class BreadthFirstSearch {
    public static void main(String[] args) {
        Node node1 = new Node(1);
        Node node2 = new Node(2);
        Node node3 = new Node(3);
        Node node4 = new Node(4);
        Node node5 = new Node(5);
        Node node6 = new Node(6);
        Node node7 = new Node(7);
        Node node8 = new Node(8);
        Node node9 = new Node(9);
        Node node10 = new Node(10);
        Node node11 = new Node(11);
        Node node12 = new Node(12);
        Node node13 = new Node(13);

        node1.addNeighbors(node11);
        node1.addNeighbors(node10);
        node1.addNeighbors(node3);
        node3.addNeighbors(node12);
        node3.addNeighbors(node4);
        node4.addNeighbors(node6);
        node6.addNeighbors(node13);
        node6.addNeighbors(node8);
        node6.addNeighbors(node7);
        node13.addNeighbors(node9);
        node7.addNeighbors(node5);
        node5.addNeighbors(node2);

        if(breadthFirstSearch(node1, node2))
            System.out.print("Yes there is a path between node "+node1.nodeNumber+ " and node "+node2.nodeNumber);
        else
            System.out.print("No there is a path between node "+node1.nodeNumber+ " and node "+node2.nodeNumber);
    }

    public static boolean breadthFirstSearch(Node source, Node destination) {
        LinkedList<Node> queue = new LinkedList<>();
        HashSet<Integer> visited = new HashSet<>();
        queue.add(source);

        while(!queue.isEmpty()) {
            Node temp = queue.remove();
            if(visited.contains(temp.nodeNumber)) continue;
            visited.add(temp.nodeNumber);

            if(temp.nodeNumber == destination.nodeNumber) return true;
            for(Node childNode : temp.nodeNeighbors)
                if(!visited.contains(childNode))
                    queue.add(childNode);
        }
        return false;
    }
}
```
