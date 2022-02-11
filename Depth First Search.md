**Depth First Search🎃**<br>
////
<br>br>

**Time complixity**<br>
The time complexity for the depth-first search is O(V+E). Where v is the number of vertices and e number of edges.<br><br>

**Explanation**<br>
Depth-first search is almost the same algorithm as breadth-first search and even both algorithms have the same time complexity, the only difference between these two is
that breadth-first search algorithms check nodes/vertices level-wise and the depth-first search goes directly into the depth of the graph.<br>
In depth-first search, there are also two main operations happing <br>
- checking all the vertices/nodes in the graph
- checking all the edges of that node <br><br>
so thus O(V+E) is the time complexity of this graph.<br><br>

Ps: in breadth first search I have already written a huge explanation about the time complexity of that graph and the same can be applied here as well. 
<br><br>

In the below coding example i have used an undirected graph, while as in breadth first search algorithm i have used the directed graph as an example. But the
graph coordinates are same in both exmaples.<br><br>

**Code**<br>
```
import java.util.ArrayList;

public class Node {
    public int nodeNumber;
    public Node parent;
    public ArrayList<Node> nodeNeighbors = new ArrayList<Node>();
    public Node(int nodeNumber) {
        this.nodeNumber = nodeNumber;
    }

    public void addNeighbors(Node node) {
        nodeNeighbors.add(node);
    }
}



import com.company.breadthFirstSearch.Node;

import java.util.ArrayList;
import java.util.HashSet;

public class DepthFirstSearch {
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

        node1.addNeighbors(node10);
        node1.addNeighbors(node11);
        node1.addNeighbors(node3);
        node10.addNeighbors(node1);
        node11.addNeighbors(node1);
        node3.addNeighbors(node1);
        node3.addNeighbors(node12);
        node3.addNeighbors(node4);
        node12.addNeighbors(node3);
        node4.addNeighbors(node3);
        node4.addNeighbors(node6);
        node6.addNeighbors(node4);
        node6.addNeighbors(node13);
        node6.addNeighbors(node8);
        node6.addNeighbors(node7);
        node13.addNeighbors(node6);
        node13.addNeighbors(node9);
        node9.addNeighbors(node13);
        node8.addNeighbors(node6);
        node7.addNeighbors(node6);
        node7.addNeighbors(node5);
        node5.addNeighbors(node7);
        node5.addNeighbors(node2);
        node2.addNeighbors(node2);

        HashSet<Node> visited = new HashSet<>();
        if(depthFirstSearch(node1, node2, visited)) {
            System.out.println("Yes There is a path between node 1 and 2");
            printThePath(node2);
        }
        else
            System.out.print("No there is not a path between node 1 and 2");
    }

    public static boolean depthFirstSearch(Node node, Node destination, HashSet<Node> visited) {
        if(visited.contains(node)) return false;
        visited.add(node);
        if(node.nodeNumber == destination.nodeNumber) return true;

        for(Node childNode: node.nodeNeighbors)
            if(!visited.contains(childNode)) {
                childNode.parent = node;
                if (depthFirstSearch(childNode, destination, visited))
                    return true;
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
