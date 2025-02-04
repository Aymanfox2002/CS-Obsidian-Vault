
## **Content:**

[[Adjacency Matrix VS Adjacency list]]
[[Directed graphs]]
[[Undirected graph]]
[[Weighted Graph]]


![[Pasted image 20250106214912.png]]


> [!NOTE] Title
> A Graph is a non-linear data structure consisting of vertices and edges. The vertices are sometimes also referred to as nodes and the edges are lines or arcs that connect any two nodes in the graph. More formally a Graph is composed of a set of vertices( **V** ) and a set of edges( **E** ). The graph is denoted by **G(V, E)**.
> - `**|V|**` = Total **number of vertices** (**nodes**) in the graph.
> - `**|E|**` = Total **number of connections** (**edges**) in the graph.

---

## **Types of graphs**

Graphs are classified based on the characteristics of their edges (**connections**).

#### `Directed Graphs`:

In **[[Directed graphs]]**, edges have a direction "arrows in image". They go from one node to another, and there is no way to return to the initial node through that edge, so you need to find an alternative path.

![[Pasted image 20250106215435.png]]


#### `Undirected Graphs`:

In [[Undirected graph]], edges are undirected (they do not have a specific direction).  You can go from one node to another and return through that same “path”.

> [!NOTE]
> When you see a diagram of a graph where the edges don’t have arrows pointing in a specific direction, you can assume that the graph is undirected.

![[Pasted image 20250106220006.png]]

#### `Weighted Graphs` :

**In weighted graphs, each edge has a value associated with it (called weight)**. This value is used to represent a certain quantifiable relationship between the nodes they connect.

For example, weights could represent **distance, time, the number of connections shared between two users in a social network,** or anything that could be used to describe the connection between nodes in the context that you are working with.

![[Pasted image 20250106220321.png]]


> [!info] Title
> These weights are used by [[Dijkstra’s Algorithm]] to optimize routes by finding the shortest or least expensive paths between nodes in a network.

#### `Unweighted Graphs` :

In contrast, unweighted graphs **do not have weights associated with their edges.** An example of this type of graph can be found in social networks, where edges represent the connection between two users. The connection cannot be quantified. Therefore, the edge has no weight.

![[Pasted image 20250106220830.png]]


> [!warning] Note
> You may have noticed that, so far, our graphs only have one edge connecting each pair of nodes. It’s natural to ask if there could be more than one edge between a pair of nodes. **A**ctually, this is possible with M**ultigraphs! T**hey can have multiple edges connecting the same pair of nodes.
> 
![[Pasted image 20250106220914.png]]

---

### **Number of Edges**

 *It’s very important to know if a graph has many or few edges because this is a crucial factor to decide how you will represent this data structure in your code. **Let’s see the different types!***

#### **Dense graphs**

**Dense graphs have many edges. But how can you determine what qualifies as “many edges”?  let’s quantify it a little bit:

👉 **Let’s find the maximum number of edges in a directed graph.** If there are `**|V|**` nodes in a directed graph (in the example below, six nodes), that means that each node can have up to `**|v|**` connections (in the example below, six connections).

Why? Because **each node could potentially connect with all other nodes and with itself** (see “loop” below)**.** Therefore, **the** **maximum number of edges that the graph can have is** `**|V|*|V|**` , which is the total number of nodes multiplied by the maximum number of connections that each node can have.

> [!important]
> **When the number of edges in the graph is close to the maximum number of edges, the graph is dense.**

![[Pasted image 20250107203424.png]]


> [!NOTE] Title
> “Loops” occur when a node has an edge that connects it to itself.

![[Pasted image 20250107203500.png]]

#### **Sparse graphs**

**Sparse Graphs have few edges.** As you can see in the diagram below, there aren’t many connections between the nodes.

![[Pasted image 20250107203919.png]]

---

### **Cycles**

You probably noticed that if you follow a sequence of connections in a graph, you may find a **path that will take you back to the same node.** This is like “walking in circles”, exactly as if you were driving around your city and you took a path that could take you back to your initial location.

**In graphs, these “circular” paths are called “cycles”.** They are **valid paths that start and end at the same node.** For example, in the diagram below, you can see that if you start at any node, you can return to that same node by following the edges.

![[Pasted image 20250107204404.png]]

> [!important]
> **Cycles are not always “isolated” because they can be part of a larger graph.** You can detect them by starting your search on a specific node and finding a path that takes you back to that same node.

![[Pasted image 20250107204457.png]]

