# [Modeling-Graphs](https://en.wikipedia.org/wiki/Graphical_model)
Modeling Graphs, Graph interface, AbstractGraph, UnweightedGraph, WeightedGraph, MST(Minimum Spanning Tree)

- The `Graph` interface defines the common operations for a graph. The Java Collections Framework serves as a good example for designing complex data structures. The common features of data structures are defined in the interfaces (e.g., Collection, Set, List, Queue), as shown in below Figure. Abstract classes (e.g., AbstractCollection, AbstractSet, AbstractList) partially implement the interfaces. Concrete classes (e.g., HashSet, LinkedHashSet, TreeSet, ArrayList, LinkedList, PriorityQueue) provide concrete implementations.
-  This design pattern is useful for modeling graphs. I will define an interface named Graph that contains all the common operations of graphs and an abstract class named AbstractGraph that partially implements the Graph interface. Many concrete graphs can be added to the design. For example, we will define such graphs named UnweightedGraph and WeightedGraph. The relationships of these interfaces and classes are illustrated in the following Figure.

<p align="center">
  <img src="https://user-images.githubusercontent.com/24220136/232947173-3b98f5c0-9eca-4252-901f-6e18c25d76fd.png" alt="Image">
</p>

- First we implement `Graph.interface`. For convenience, we assume the graph is a simple graph, i.e., a vertex has no edge to itself and there are no parallel edges from vertex u to v.
- `AbstractGraph` implements all the methods from Graph, and it does not introduce any new methods except a convenient `addEdge(edge)` method that adds an Edge object to the adjacency edge list.
- `UnweightedGraph` simply extends `AbstractGraph` with five constructors for creating the concrete Graph instances.
- Finally with the `TestGraph.java` we check the successful implementation in the following UML diagram:

<p align="center">
  <img src="https://user-images.githubusercontent.com/24220136/232947459-1bd44e39-d65f-41ab-b5a3-11fa3baa53d1.png" alt="Image">
</p>

- The program creates `graph1` for the graph in lines 3–23. The vertices for graph1 are defined in lines 3–5. The edges for graph1 are defined in 8–21.
- The edges are represented using a two-dimensional array. For each row i in the array, edges[i][0] and edges[i][1] indicate that there is an edge from vertex edges[i][0] to vertex edges[i][1]. For example, the first row, {0, 1}, represents the edge from vertex 0 (edges[0][0]) to vertex 1 (edges[0][1]). The row {0, 5} represents the edge from vertex 0 (edges[2][0]) to vertex 5 (edges[2][1]).
- The graph is created in line 23. Line 31 invokes the `printEdges()` method on graph1 to display all edges in graph1.
- The program creates `graph2` for the graph in lines 34–43. The edges for graph2 are defined in lines 37–40. graph2 is created using a list of Edge objects in line 43.
- Line 47 invokes the `printEdges()` method on graph2 to display all edges in graph2. Note that both graph1 and graph2 contain the vertices of strings. The vertices are associated with indices 0, 1, . . . , n-1. The index is the location of the vertex in vertices. For example, the index of vertex Miami is 9.
- The `AbstractGraph` class defines the data field vertices (line 4) to store vertices and neighbors (line 5) to store edges in adjacency lists. `neighbors.get(i)` stores all edges adjacent to vertex i.
- Four overloaded constructors are defined in lines 9–42 to create a default graph, or a graph from arrays or lists of edges and vertices. The createAdjacencyLists(int[][] edges, int numberOfVertices) method creates adjacency lists from edges in an array (lines 45–50). The createAdjacencyLists(List<Edge> edges, int numberOfVertices)
method creates adjacency lists from edges in a list (lines 53–58).
- The `getNeighbors(u)` method (lines 81–87) returns a list of vertices adjacent to vertex u. The clear() method (lines 106–110) removes all vertices and edges from the graph. The addVertex(u) method (lines 112–122) adds a new vertex to vertices and returns true. It returns false if the vertex is already in the graph (line 120).
- The `addEdge(e)` method (lines 124–139) adds a new edge the adjacency edge list and returns true. It returns false if the edge is already in the graph. This method may throw IllegalArgumentExcepiton if the edge is invalid (lines 126–130).
- The `printEdges()` method (lines 95–104) displays all vertices and edges adjacent to each vertex.
- The code in lines 164–293 gives the methods for finding a depth-first search tree and a breadth-first search tree, which will be introduced in Sections 28.7 and 28.9, respectively. 
- Following is the Demo run of the `TestGraph.java`:

<p align="center">
  <img src="https://user-images.githubusercontent.com/24220136/232948145-62b42f14-44c7-45c8-88ee-23cfcc67e18f.png" alt="Image">
</p>
  
## [Graph Visualization](https://en.wikipedia.org/wiki/Graph_drawing)

- To display a graph visually, each vertex must be assigned a location. The following `ModelingGraphs` directory introduces how to model a graph using the Graph interface, AbstractGraph class, and UnweightedGraph class. And shows how to display graphs graphically.
- In order to display a graph, we need to know where each vertex is displayed and the name of each vertex. To ensure a graph can be displayed, we define an interface named Displayable that has the methods for obtaining the x- and y-coordinates and
their names, and make vertices instances of Displayable.
- The class City is defined to model the vertices with their coordinates and names (lines 39–63).
- The program creates a graph with the vertices of the City type (line 30). Since City implements Displayable, a `GraphView` object created for the graph displays the graph in the pane (line 33).
- Output result is as following:

<p align="center">
  <img src="https://user-images.githubusercontent.com/24220136/232974787-69e94426-51c5-4e6d-a78e-60a9c0283474.png" alt="Image">
</p>
  
## [Weighted Graph](https://www.wikidata.org/wiki/Q1723971)

- `WeightedGraph` simply extends `AbstractGraph` with five constructors for creating concrete WeightedGraph instances. WeightedGraph inherits all methods from AbstractGraph, overrides the clear and addVertex methods, implements a new addEdge method for adding a weighted edge, and also introduces new methods for obtaining minimum spanning trees and for finding all single-source shortest paths.

<p align="center">
  <img src="https://user-images.githubusercontent.com/24220136/233539981-eeda8a6f-f8a7-4eb1-8c3f-be7e78169d88.png" alt="Image">
</p>

- WeightedGraph java api is given in following folder: `WeightedGraph`. The WeightedGraph class extends the AbstractGraph class (line 3). The properties vertices and neighbors in AbstractGraph are inherited in WeightedGraph. neighbors is a list. Each element is the list is another list that contains edges.
- For unweighted graph, each edge is an instance of AbstractGraph.Edge. For a weighted graph, each edge is an instance of WeightedEdge. WeightedEdge is a subtype of Edge. So you can add a weighted edge into neighbors.get(i) for a weighted graph (line 47).

- Following is the demo run output:

<p align="center">
  <img src="https://user-images.githubusercontent.com/24220136/233540195-f836f8d6-3105-4bbc-bf50-694e62c3851f.png" alt="Image">
</p>

## [MST(Minimum Spanning Tree)](https://en.wikipedia.org/wiki/Minimum_spanning_tree)
  
- The `getMinimumSpanningTree` (int v) method is defined in the `WeightedGraph` class. It returns an instance of the MST class. The `MST` class is defined as an inner class in the `WeightedGraph` class, which extends the `Tree` class. The MST class was implemented in lines 141–153 in `WeightedGraph` class. Source code `TestMST.java` is located inside the `WeightedGraph directory`.

<p align="center">
  <img src="https://user-images.githubusercontent.com/24220136/233544533-39ea209a-e41f-4016-b84d-ba4bc3de869a.png" alt="Image">
</p>

- The `TestMST.java` program creates a weighted graph in line 27. It then invokes `getMinimumSpanningTree()` (line 28) to return an MST that represents a minimum spanning tree for the graph. Invoking `printTree()` (line 30) on the MST object displays the edges in the tree. Note that MST is a subclass of Tree. The printTree() method is defined in the Tree class.

- The graphical illustration of the minimum spanning tree is shown in below given Figure. The vertices are added to the tree in this order: Seattle, San Francisco, Los Angeles, Denver, Kansas City, Dallas, Houston, Chicago, New York, Boston, Atlanta, and Miami.

 <p align="center">
  <img src="https://user-images.githubusercontent.com/24220136/233544795-1bb76df2-cf54-4989-905f-9de0f05b5d19.png" alt="Image">
</p> 
  
- Demo run output result:
  
 <p align="center">
  <img src="https://user-images.githubusercontent.com/24220136/233544843-da6d7df6-c0e8-4acd-8ea1-0d62b55f0754.png" alt="Image">
</p>
