# Graphs

[Reading](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/graphs.html)

A graph is a non-linear data structure that can be looked at as a collection of `vertices` (or `nodes`) potentially connected by line segments named `edges`.

Here is some common terminology used when working with Graphs:

1. Vertex - A vertex, also called a “node”, is a data object that can have zero or more adjacent vertices.
2. Edge - An edge is a connection between two nodes.
3. Neighbor - The neighbors of a node are its adjacent nodes, i.e., are connected via an edge.
4. Degree - The degree of a vertex is the number of edges connected to that vertex.

An `Undirected Graph` is a graph where each edge is undirected or bi-directional. This means that the undirected graph does not move in any direction.

A `Directed Graph` also called a `Digraph` is a graph where every edge is directed.

Unlike an undirected graph, a `Digraph` has direction. Each node is directed at another node with a specific requirement of what node should be referenced next.

### Complete vs Connected vs Disconnected

A complete graph is when all nodes are connected to all other nodes.

A connected graph is graph that has all of `vertices`/`nodes` have at least one edge.

A disconnected graph is a graph where some vertices may not have edges.

### Acyclic vs Cyclic

An acyclic graph is a directed graph without cycles.

A cycle is when a node can be traversed through and potentially end up back at itself.

A Cyclic graph is a graph that has cycles.

A cycle is defined as a path of a positive length that starts and ends at the same vertex.

### Graph Representation

We represent graphs through:

* Adjacency Matrix
* Adjacency List

An Adjacency matrix is represented through a 2-dimensional array. If there are n vertices, then we are looking at an n x n Boolean matrix

Each Row and column represents each vertex of the data structure. The elements of both the column and the row must add up to 1 if there is an edge that connects the two, or zero if there isn’t a connection.

a sparse graph is when there are very few connections. a dense graph is when there are many connections.

Within an adjacency matrix, an undirected graph will always be symmetric. This is not the case for a directed graph.

An adjacency list is the most common way to represent graphs.

An adjacency list is a collection of linked lists or array that lists all of the other vertices that are connected.

Adjacency lists make it easy to view if one vertices connects to another.

### Weighted Graphs

When representing a weighted graph in a matrix, you set the element in the 2D array to represent the actual weight between the two paths. If there is not a connection between the two vertices, you can put a `0`, although it is known for some people to put the infinity sign instead.

### Traversals

Graphs are able to be traversed. The traversals itself are like those of trees. Below is a breakdown of how you would traverse a graph

#### Breadth First

In a breadth first traversal, you are starting at a specific vertex/node. This node must be specified when calling the `BreadthFirst()` method. The breadth first traversal of a graph is like that of a tree, with the exception that graphs can have cycles. Traversing a graph that has cycles will result in an infinite loop….this is bad. To prevent such behavior, we need to have some way to keep track of whether a vertex has been “visited” before. Upon each visit, we’ll add the previously-unvisited vertex to a `visited` set, so we know not to visit it again as traversal continues.

As a refresher of what breadth first actually means here it is: Breadth first traversal is when you visit all the nodes that are closest to the root as possible. From there you traverse outwards, level by level, until you have visited all the vertices/nodes.

Here is what the algorithm breadth first traversal looks like:

`Enqueue` the declared start node into the Queue.
Create a loop that will run while the node still has nodes present.
`Dequeue` the first node from the queue
if the `Dequeue`‘d node has unvisited child nodes, add the unvisited children to `visited` set and insert them into the queue.

Example code:
```
ALGORITHM BreadthFirst(vertex)
    DECLARE nodes <-- new List()
    DECLARE breadth <-- new Queue()
    DECLARE visited <-- new Set()

    breadth.Enqueue(vertex)
    visited.Add(vertex)

    while (breadth is not empty)
        DECLARE front <-- breadth.Dequeue()
        nodes.Add(front)

        for each child in front.Children
            if(child is not visited)
                visited.Add(child)
                breadth.Enqueue(child)

    return nodes;
```

Here is a breakdown of what is going on:

1. We have declared that our starting node (or root) is going to be `Node A`.
2. The first thing we want to do is `Enqueue` the root.
3. We also need to add the root to the `visited` set.
4. Next, we enter a while loop. We want this loop to keep running until there are no more nodes in our queue.
5. Once we are in the while loop, we want to Dequeue the front node and then check to see if it has any children.
6. If there are children of the node we are currently looking at, we want to add them to visited set. This will help us know that we have already seen that node before, and won’t accidently push us into an infinite loop if the graph was cyclic. In addition to tracking each child node as visited, we want to place any of its children that have not yet been visited into the queue.
7. The process will complete until the queue is empty.
8. Once the while loop breaks, we can then return the list of nodes. This list will contain, in order, all the nodes that were traversed.


A few things to note about breadth first traversals:

* If there are any disconnected nodes (such as islands) with the graph data structure, they will not be traversed.
* Breadth first only outputs the nodes that are connected in some relation to the root that you pass in.

#### Depth First

In a depth first traversal, our approach is a bit different than the approach used for breadth first. While the breadth first traversal uses a Queue to visit all children at a given level, the depth first traversal uses a Stack to visit all children of a given subtree. (This differs from our approach to tree traversal, where we visit nodes via recursive calls. Recursive calls use a call stack internally.)

The algorithm for a depth first traversal is as follows:

1. `Push` the root node into the Stack and mark as visited.
2. Start a while loop that runs as long as the stack is not empty.
3. `Pop` the top node off of the stack and check its neighbors.
4. If a neighbor hasn’t been visited, push it onto the stack and mark as visited.
5. Repeat until the stack is empty.

### Real World Uses of Graphs

Graphs are extremely popular when it comes to it’s uses. Here are just a few examples of graphs in use:

* GPS and Mapping
* Driving Directions
* Social Networks
* Airline Traffic
* Netflix uses graphs for suggestions of products

[Back](README.md)