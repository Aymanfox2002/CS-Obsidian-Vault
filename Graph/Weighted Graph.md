![[Pasted image 20250106220321.png]]

> [!info]
> A **weighted graph** is a graph where each edge has a **weight** (or cost) associated with it. These weights can represent distances, costs, time, or any other metric depending on the application.

---
## **Implementing**

```
class WeightedGraph {
    constructor() {
        this.adjacencyList = new Map();
    }

    // Add a vertex to the graph
    addVertex(vertex) {
        if (!this.adjacencyList.has(vertex)) {
            this.adjacencyList.set(vertex, []);
        }
    }

    // Add a weighted edge between two vertices
    addEdge(vertex1, vertex2, weight) {
        if (!this.adjacencyList.has(vertex1)) {
            this.addVertex(vertex1);
        }
        if (!this.adjacencyList.has(vertex2)) {
            this.addVertex(vertex2);
        }
        this.adjacencyList.get(vertex1).push({ node: vertex2, weight });
        this.adjacencyList.get(vertex2).push({ node: vertex1, weight }); // Undirected graph
    }

    // Print the graph
    print() {
        for (let [vertex, edges] of this.adjacencyList) {
            console.log(`${vertex} -> ${edges.map(e => `${e.node}(${e.weight})`).join(', ')}`);
        }
    }
}

const graph = new WeightedGraph();

// Add vertices
graph.addVertex('A');
graph.addVertex('B');
graph.addVertex('C');
graph.addVertex('D');

// Add weighted edges
graph.addEdge('A', 'B', 4);
graph.addEdge('A', 'C', 2);
graph.addEdge('B', 'C', 1);
graph.addEdge('B', 'D', 5);
graph.addEdge('C', 'D', 8);

// Print the graph
graph.print();
// Output:
// A -> B(4), C(2)
// B -> A(4), C(1), D(5)
// C -> A(2), B(1), D(8)
// D -> B(5), C(8)
```

*Here’s the final weighted graph looks like*

```
A --4-- B --5-- D
|      /       |
2    1         8
|  /           |
C -------------- 
```

**Vertices**: `A`, `B`, `C`, `D`.

**Edges**:

A -> B (Weight: `4`)

A -> C (Weight: `2`)

B -> C (Weight: `1`)

B -> D (Weight: `5`)

C -> D (Weight: `8`)

---
