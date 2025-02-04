
> [!NOTE] Definition
> A directed graph (or digraph) is a set of vertices connected by edges, where the edges have a direction associated with them. This means that if there is an edge from vertex A to vertex B, it does not imply there is an edge from vertex B to vertex A.

![[Pasted image 20250106214912.png]]

---

## **Key Terms:**

- **Vertex (Node)**: A fundamental part of the graph that holds data.
- **Edge (Arc)**: A connection between two vertices, with a direction from one vertex to another.

---

## **Implementation**

```
class Graph {
  constructor() {
    this.adjacencyList = {};
  }

  // Add a vertex to the graph
  addVertex(vertex) {
    if (!this.adjacencyList[vertex]) {
      this.adjacencyList[vertex] = [];
    }
  }

  // Add a directed edge from vertex1 to vertex2
  addEdge(vertex1, vertex2) {
    if (this.adjacencyList[vertex1]) {
      this.adjacencyList[vertex1].push(vertex2);
    }
  }

  // Remove an edge from vertex1 to vertex2
  removeEdge(vertex1, vertex2) {
    if (this.adjacencyList[vertex1]) {
      this.adjacencyList[vertex1] = this.adjacencyList[vertex1].filter(
        (v) => v !== vertex2
      );
    }
  }

  // Remove a vertex and all its edges
  removeVertex(vertex) {
    while (this.adjacencyList[vertex]) {
      const adjacentVertex = this.adjacencyList[vertex].pop();
      this.removeEdge(adjacentVertex, vertex);
    }
    delete this.adjacencyList[vertex];
  }
}


const graph = new Graph();

// Add vertices
graph.addVertex('A');
graph.addVertex('B');
graph.addVertex('C');
graph.addVertex('D');

// Add directed edges
graph.addEdge('A', 'B');
graph.addEdge('A', 'C');
graph.addEdge('B', 'D');
graph.addEdge('C', 'D');
graph.addEdge('D', 'A'); // Example of creating a cycle

```

---

### **Direct Graph Traversal**

#### **Depth-First Search (DFS)**

```
  // Depth-First Search
  dfs(start) {
    const visited = {};
    const result = [];
    const adjacencyList = this.adjacencyList;

    (function dfsHelper(vertex) {
      if (!vertex) return;
      visited[vertex] = true;
      result.push(vertex);
      adjacencyList[vertex].forEach((neighbor) => {
        if (!visited[neighbor]) {
          dfsHelper(neighbor);
        }
      });
    })(start);

    return result;
  }
```

##### *Example Usage*

Graph Structure

```
    A
   / \
  B   C
 / \   \
D   E   F
```

### DFS Traversal Steps from Vertex "A"

1. **Start at Vertex "A"**:
    
    - Visit `A`
        
    - Mark `A` as visited
        
    - Add `A` to the result list
        
    - Current path: `[A]`
        
2. **Explore Neighbors of "A" (B and C)**:
    
    - Visit `B` (left child of `A`)
        
    - Mark `B` as visited
        
    - Add `B` to the result list
        
    - Current path: `[A, B]`
        
3. **Explore Neighbors of "B" (D and E)**:
    
    - Visit `D` (left child of `B`)
        
    - Mark `D` as visited
        
    - Add `D` to the result list
        
    - Current path: `[A, B, D]`
        
4. **D has no neighbors, backtrack to "B" and explore "E"**:
    
    - Visit `E` (right child of `B`)
        
    - Mark `E` as visited
        
    - Add `E` to the result list
        
    - Current path: `[A, B, D, E]`
        
5. **E has no neighbors, backtrack to "A" and explore "C"**:
    
    - Visit `C` (right child of `A`)
        
    - Mark `C` as visited
        
    - Add `C` to the result list
        
    - Current path: `[A, B, D, E, C]`
        
6. **Explore Neighbors of "C" (F)**:
    
    - Visit `F` (right child of `C`)
        
    - Mark `F` as visited
        
    - Add `F` to the result list
        
    - Current path: `[A, B, D, E, C, F]`
        
7. **F has no neighbors and no more vertices to explore**:
    
    - DFS traversal is complete

---
#### **Breadth-First Search (BFS)**

```
bfs(start) {
    const queue = [start];
    const visited = { [start]: true };
    const result = [];
    const adjacencyList = this.adjacencyList;

    while (queue.length) {
      const vertex = queue.shift();
      result.push(vertex);

      adjacencyList[vertex].forEach((neighbor) => {
        if (!visited[neighbor]) {
          visited[neighbor] = true;
          queue.push(neighbor);
        }
      });
    }

    return result;
  }
```


##### *Example Usage*

```
    A
   / \
  B   C
 / \   \
D   E   F

```

### BFS Traversal Steps from Vertex "A"

1. **Start at Vertex "A"**:
    
    - Visit `A`
        
    - Mark `A` as visited
        
    - Add `A` to the result list
        
    - Enqueue neighbors `B` and `C`
        
    - Queue: `[B, C]`
        
    - Result: `[A]`
        
2. **Dequeue and Visit Vertex "B"**:
    
    - Dequeue `B`
        
    - Visit `B`
        
    - Mark `B` as visited
        
    - Add `B` to the result list
        
    - Enqueue neighbors `D` and `E`
        
    - Queue: `[C, D, E]`
        
    - Result: `[A, B]`
        
3. **Dequeue and Visit Vertex "C"**:
    
    - Dequeue `C`
        
    - Visit `C`
        
    - Mark `C` as visited
        
    - Add `C` to the result list
        
    - Enqueue neighbor `F`
        
    - Queue: `[D, E, F]`
        
    - Result: `[A, B, C]`
        
4. **Dequeue and Visit Vertex "D"**:
    
    - Dequeue `D`
        
    - Visit `D`
        
    - Mark `D` as visited
        
    - Add `D` to the result list
        
    - `D` has no unvisited neighbors
        
    - Queue: `[E, F]`
        
    - Result: `[A, B, C, D]`
        
5. **Dequeue and Visit Vertex "E"**:
    
    - Dequeue `E`
        
    - Visit `E`
        
    - Mark `E` as visited
        
    - Add `E` to the result list
        
    - `E` has no unvisited neighbors
        
    - Queue: `[F]`
        
    - Result: `[A, B, C, D, E]`
        
6. **Dequeue and Visit Vertex "F"**:
    
    - Dequeue `F`
        
    - Visit `F`
        
    - Mark `F` as visited
        
    - Add `F` to the result list
        
    - `F` has no unvisited neighbors
        
    - Queue: `[]`
        
    - Result: `[A, B, C, D, E, F]`