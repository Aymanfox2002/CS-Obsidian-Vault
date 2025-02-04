## **Adjacency Matrix**


> [!info]
> An **adjacency matrix** is a 2D array (matrix) where each cell `matrix[i][j]` represents whether there is an edge between vertex `i` and vertex `j`. For weighted graphs, the cell contains the weight of the edge; for unweighted graphs, it typically contains `1` (edge exists) or `0` (no edge).

---
### Example

*Consider the following graph:*

```
A -- B
|    |
C -- D
```

*The adjacency matrix for this graph is:*

| ""  | A   | B   | C   | D   |
| --- | --- | --- | --- | --- |
| A   | 0   | 1   | 1   | 0   |
| B   | 1   | 0   | 0   | 1   |
| C   | 1   | 0   | 0   | 1   |
| D   | 0   | 1   | 1   | 0   |
 `1` indicates an edge exists between the vertices.
 
 `0` indicates no edge.

> For a **weighted graph**, the matrix would contain the edge weights instead of `1`s and `0`s.

---

## **Adjacency List**

> [!info]
> An **adjacency list** is a collection of lists or arrays where each vertex stores a list of its adjacent vertices. For weighted graphs, the list also includes the edge weights.

---

### Example

*Using the same graph as above:*

```
{
    A: ['B', 'C'],
    B: ['A', 'D'],
    C: ['A', 'D'],
    D: ['B', 'C']
}
```

*For a **weighted graph**, the adjacency list would look like this:*

---
## **Adjacency Matrix** VS **Adjacency List**

| Feature               | Adjacency Matrix                          | Adjacency List                           |
| --------------------- | ----------------------------------------- | ---------------------------------------- |
| **Space Complexity**  | **$O(V^2)$**   *(V = number of vertices)* | **$O(V+E)$** *(E = number of edges)*     |
| **Edge Lookup Time**  | **$O(1)$** *(constant time)*              | **$O(V)$** *(linear time in worst case)* |
| **Memory Efficiency** | Inefficient for sparse graphs             | Efficient for sparse graphs              |
| **Ease of Iteration** | Easy to iterate over all edges            | Requires iterating over all lists        |
| **Weighted Graphs**   | Easy to represent                         | Easy to represent                        |
| **Directed Graphs**   | Easy to represent                         | Easy to represent                        |

---

## **When to Use?**

### Use an **Adjacency Matrix** when:

- The graph is **dense** (i.e., the number of edges is close to $V^2$).
    
- You need **frequent edge lookups** (e.g., checking if an edge exists between two vertices).
    
- The graph is **small** (space is not a concern).
    

### Use an **Adjacency List** when:

- The graph is **sparse** (i.e., the number of edges is much less than $V^2$).
    
- You need to **traverse the graph** (e.g., DFS, BFS).
    
- Memory usage is a concern (e.g., for large graphs).


---

## **Pros and Cons**

#### **Adjacency Matrix**

**`Pros:`**

1. Fast edge lookup: Checking if an edge exists between two vertices is $O(1)$.
2. Easy to implement: Simple 2D array structure.
3. Space-efficient for dense graphs: When $E≈V^2$, the space complexity is justified.


**`Cons:`**

1. High space complexity: Requires $O(V^2)$ space, which is inefficient for sparse graphs.
2. Slow iteration: Iterating over all edges takes $O(V^2)$ time.


---

#### **Adjacency List**

**`Pros:`**

1. Space-efficient for sparse graphs: Requires $O(V+E)$ space.
2. Efficient traversal: Iterating over neighbors of a vertex is fast.
3. Scalable: Works well for large graphs.


**`Cons:`**

1. Slower edge lookup: Checking if an edge exists takes $O(V)$ in the worst case.
2. Slightly more complex: Requires managing lists or arrays for each vertex.

