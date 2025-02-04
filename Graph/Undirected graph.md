![[Pasted image 20250106220006.png]]

> [!info] Info
> An **undirected graph** is a set of vertices (or nodes) connected by edges, where the edges have no direction. This means that if there is an edge between vertex `A` and vertex `B`, you can traverse from `A` to `B` and from `B` to `A`.

---
### **Key Concepts:**

1. **Vertices (Nodes)**: The fundamental units of the graph.
2. **Edges**: Connections between vertices.
3. **Adjacency List**: A common way to represent a graph, where each vertex stores a list of its adjacent vertices.

---
### **Implementing**

```
class Graph {
    constructor() {
        this.adjacencyList = new Map();
    }

    // Add a vertex to the graph
    addVertex(vertex) {
        if (!this.adjacencyList.has(vertex)) {
            this.adjacencyList.set(vertex, []);
        }
    }

    // Add an edge between two vertices
    addEdge(vertex1, vertex2) {
        if (!this.adjacencyList.has(vertex1)) {
            this.addVertex(vertex1);
        }
        if (!this.adjacencyList.has(vertex2)) {
            this.addVertex(vertex2);
        }
        this.adjacencyList.get(vertex1).push(vertex2);
        this.adjacencyList.get(vertex2).push(vertex1); // Since it's undirected
    }

    // Remove an edge between two vertices
    removeEdge(vertex1, vertex2) {
        this.adjacencyList.set(
            vertex1,
            this.adjacencyList.get(vertex1).filter(v => v !== vertex2)
        );
        this.adjacencyList.set(
            vertex2,
            this.adjacencyList.get(vertex2).filter(v => v !== vertex1)
        );
    }

    // Remove a vertex from the graph
    removeVertex(vertex) {
        while (this.adjacencyList.get(vertex).length) {
            const adjacentVertex = this.adjacencyList.get(vertex).pop();
            this.removeEdge(vertex, adjacentVertex);
        }
        this.adjacencyList.delete(vertex);
    }

    // Print the graph
    print() {
        for (let [vertex, edges] of this.adjacencyList) {
            console.log(`${vertex} -> ${edges.join(', ')}`);
        }
    }
}

const graph = new Graph();

// Add vertices
graph.addVertex('A');
graph.addVertex('B');
graph.addVertex('C');
graph.addVertex('D');

// Add edges
graph.addEdge('A', 'B');
graph.addEdge('A', 'C');
graph.addEdge('B', 'D');
graph.addEdge('C', 'D');

// Print the graph
graph.print();
// Output:
// A -> B, C
// B -> A, D
// C -> A, D
// D -> B, C

// Remove an edge
graph.removeEdge('A', 'C');
graph.print();
// Output:
// A -> B
// B -> A, D
// C -> D
// D -> B, C

// Remove a vertex
graph.removeVertex('D');
graph.print();
// Output:
// A -> B
// B -> A
// C -> 
```

---

### **[[Undirect Graph Traversing]]**

#### **Depth-First Search (DFS)**

```
class Graph {
    // ... (previous code)

    dfs(start) {

    const visited = new Set(); // Tracks visited vertices

    const result = []; // Stores the order of traversal

  

    const dfsHelper = (vertex) => {

      // Base case: if the vertex is null or already visited, return

      if (!vertex) return null;

      visited.add(vertex); // Mark the vertex as visited

      result.push(vertex); // Add it to the result

      // Recursively visit all unvisited neighbors

      this.adjacencyList.get(vertex).forEach((neighbor) => {

        if (!visited.has(neighbor)) {

          return dfsHelper(neighbor);

        }

      });

    };

    // Start DFS from the given vertex

    dfsHelper(start);

    return result; // Return the traversal order

  }
    
}

const graph = new Graph();
graph.addEdge('A', 'B');
graph.addEdge('A', 'C');
graph.addEdge('B', 'D');
graph.addEdge('C', 'D');

console.log(graph.dfs('A')); // Output: [ 'A', 'B', 'D', 'C' ]
```

##### *Example Usage*

Let’s create a graph and perform DFS:

```
const graph = new Graph();
graph.addEdge('A', 'B');
graph.addEdge('A', 'C');
graph.addEdge('B', 'D');
graph.addEdge('C', 'D');

console.log(graph.dfs('A')); // Output: [ 'A', 'B', 'D', 'C' ]
```

##### *Step-by-Step Explanation of the Example:*

1. **Start at `A`**:
    
    - Mark `A` as visited.
        
    - Add `A` to the result: `['A']`.
        
    - Visit `A`'s neighbors: `['B', 'C']`.
        
2. **Visit `B`**:
    
    - Mark `B` as visited.
        
    - Add `B` to the result: `['A', 'B']`.
        
    - Visit `B`'s neighbors: `['A', 'D']`.
        
        - `A` is already visited, so skip it.
            
        - Visit `D`.
            
3. **Visit `D`**:
    
    - Mark `D` as visited.
        
    - Add `D` to the result: `['A', 'B', 'D']`.
        
    - Visit `D`'s neighbors: `['B', 'C']`.
        
        - `B` is already visited, so skip it.
            
        - Visit `C`.
            
4. **Visit `C`**:
    
    - Mark `C` as visited.
        
    - Add `C` to the result: `['A', 'B', 'D', 'C']`.
        
    - Visit `C`'s neighbors: `['A', 'D']`.
        
        - Both `A` and `D` are already visited, so backtrack.
            
5. **Backtrack**:
    
    - All vertices have been visited, so the traversal ends.



---

#### **Breadth-First Search (BFS)**

```
class Graph {
    // ... (previous code)

    bfs(start) {
        const queue = [start];
        const visited = new Set();
        const result = [];
        visited.add(start);

        while (queue.length) {
            const vertex = queue.shift();
            result.push(vertex);
            this.adjacencyList.get(vertex).forEach(neighbor => {
                if (!visited.has(neighbor)) {
                    visited.add(neighbor);
                    queue.push(neighbor);
                }
            });
        }

        return result;
    }
}

const graph = new Graph();
graph.addEdge('A', 'B');
graph.addEdge('A', 'C');
graph.addEdge('B', 'D');
graph.addEdge('C', 'D');

console.log(graph.bfs('A')); // Output: [ 'A', 'B', 'C', 'D' ]
```

##### *Example Usage*

```
    A
   / \
  B   C
 / \   \
D   E   F
```

#### BFS Traversal from Vertex `A`

1. **Start at `A`**:
    
    - Queue: `[A]`
    - Visited: `{A}`
    - Result: `[]`
2. **Dequeue `A`, visit neighbors `B` and `C`**:
    
    - Queue: `[B, C]`
    - Visited: `{A, B, C}`
    - Result: `[A]`
3. **Dequeue `B`, visit neighbors `D` and `E`**:
    
    - Queue: `[C, D, E]`
    - Visited: `{A, B, C, D, E}`
    - Result: `[A, B]`
4. **Dequeue `C`, visit neighbor `F`**:
    
    - Queue: `[D, E, F]`
    - Visited: `{A, B, C, D, E, F}`
    - Result: `[A, B, C]`
5. **Dequeue `D`**:
    
    - Queue: `[E, F]`
    - Visited: `{A, B, C, D, E, F}`
    - Result: `[A, B, C, D]`
6. **Dequeue `E`**:
    
    - Queue: `[F]`
    - Visited: `{A, B, C, D, E, F}`
    - Result: `[A, B, C, D, E]`
7. **Dequeue `F`**:
    
    - Queue: `[]`
    - Visited: `{A, B, C, D, E, F}`
    - Result: `[A, B, C, D, E, F]`

### Final BFS Traversal Order

`[A, B, C, D, E, F]`

