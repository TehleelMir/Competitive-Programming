**Breadth-First Search🛒**<br>
Breadth-first search is a graph algorithm used to <br>
- To check if there is a path between two vertices/nodes
- To get the shortest path between two nodes
- To do a traversal of a whole graph i.e. visiting each node in the given graph.

<br>

**Time complixty**<br>
The time complexity of the breadth-first search algorithm is O(v+e). Where v is the number of vertices/nodes and e is for the number of edges. <br><br>

**Explanation**<br>
Let's take an example, suppose we want to see if there exists a path between two nodes in a graph, and in the worst case the node "b" can be at the end 
of the graph, so we have to go through each node in the graph first, to reach that one. And the time complexity for that will O(n) where n is the number
of vertices/node we have in a graph which we can also write as O(v). <br>
While traversing through each node we have to check its "neighbor's or you can say its edges" as well. So example if a node "c" has 3 edges/neighbors
attached to it, we have to perform 3 operations on node "c". And the time complexity for that will be again O(n) where n is the number of edges that a particular node 
have, which we can also write as O(e). <br><br>
Combining the both we get the total time complexity of O(V+E) <br>
- (V: because we are going to visit every node in the worst case)
- (E: Total number of edges a graph have because on each node we have to visit/check its edges as well.

<br>
<br>
The below coding example is checking if there is a path between node (1) and node (2), in a directed graph. And if there is 
it will print the path between those two nodes, and again that path will be the shortest path possible between these two nodes.
<br>
<br>
<p align="center">
  <img src="https://github.com/TehleelMir/images/blob/main/graph.jpeg" width="350"/>
</p>
<br>
<br>

**Code**<br>
```
import java.util.ArrayList;

class Node {
    int nodeNumber;
    Node parent;
    ArrayList<Node> nodeNeighbors = new ArrayList<Node>();
    public Node(int nodeNumber) {
        this.nodeNumber = nodeNumber;
    }

    public void addNeighbors(Node node) {
        nodeNeighbors.add(node);
    }
}



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
            System.out.println("Yes there is a path between node "+node1.nodeNumber+ " and node "+node2.nodeNumber);
        else
            System.out.println("No there is a path between node "+node1.nodeNumber+ " and node "+node2.nodeNumber);
    }

    public static boolean breadthFirstSearch(Node source, Node destination) {
        LinkedList<Node> queue = new LinkedList<>();
        HashSet<Integer> visited = new HashSet<>();
        queue.add(source);
        source.parent = null;

        while(!queue.isEmpty()) {
            Node temp = queue.remove();
            if(visited.contains(temp.nodeNumber)) continue;
            visited.add(temp.nodeNumber);

            if(temp.nodeNumber == destination.nodeNumber) {
                printThePath(temp);
                return true;
            }
            for(Node childNode : temp.nodeNeighbors)
                if(!visited.contains(childNode.nodeNumber)) {
                    childNode.parent = temp;
                    queue.add(childNode);
                }
        }
        return false;
    }

    public static void printThePath(Node node) {
        ArrayList<Node> path = new ArrayList<>();
        while(node != null) {
            path.add(node);
            node = node.parent;
        }

        for(int i=path.size()-1 ; i>-1 ; i--)
            if(i == 0)  System.out.println(path.get(i).nodeNumber);
            else        System.out.print(path.get(i).nodeNumber + " -> ");
    }
}
```
