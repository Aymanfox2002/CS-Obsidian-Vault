**[[Binary Tree]]**
#### **Contents :-**

---



> [!NOTE] Info
> The Tree data structure is similar to Linked Lists in that each node contains data and can be linked to other nodes.
> We have previously covered data structures like Arrays, Linked Lists, Stacks, and Queues. These are all linear structures, which means that each element follows directly after another in a sequence. Trees however, are different. In a Tree, a single element can have multiple 'next' elements, allowing the data structure to branch out in various directions.

---

#### **The Tree data structure can be useful in many cases:**

- **Hierarchical Data:** File systems, organizational models, etc.
- **Databases:** Used for quick data retrieval.
- **Routing Tables:** Used for routing data in network algorithms.
- **Sorting/Searching**: Used for sorting data and searching for data.
- **Priority Queues:** Priority queue data structures are commonly implemented using trees, such as binary heaps.

---

#### **Tree Terminology and Rules**



![[Treedatastructure.png]]

- The first node in a tree is called the **root** node.
- A link connecting one node to another is called an **<mark class="hltr-r">edge</mark>**.
- A **parent** node has links to its **child** nodes. Another word for a parent node is **internal** node.
- A node can have zero, one, or many child nodes.
- A node can only have one parent node.
- Nodes without links to other child nodes are called **<mark class="hltr-r">leaves</mark>**, or **leaf nodes**.
- The **<mark class="hltr-r">tree height</mark>** is the maximum number of edges from the root node to a leaf node. The height of the tree above is 4.
-  when you know the level's node this call **<mark class="hltr-r">depth of a node</mark>**
- The **height of a node** is the maximum number of edges between the node and a leaf node.
- The **tree size** is the number of nodes in the tree.
- The nodes from the same parent it's called **siblings**
- In the context of trees, an **<mark class="hltr-r">ancestor</mark>** of a node is any node that is on the path from the root to that node. This includes the node itself, its parent, its grandparent, and so on, all the way up to the root of the tree.

For example, in a binary tree:
```
      A
     / \
    B   C
   / \
  D   E
```
- Node `A` is an ancestor of nodes `B`, `C`, `D`, and `E`.
- Node `B` is an ancestor of nodes `D` and `E`.
- Node `D` has no ancestors other than itself.

Ancestors are crucial in various tree operations, such as finding the lowest common ancestor of two nodes, which is a common problem in computer science.

If you're interested in learning more about tree structures, you might find this [video](https://www.youtube.com/watch?v=1BfVu4hmSmE&list=PLwCMLs3sjOY4UQq4vXgGPwGLVX1Y5faaS&index=24) helpful.


---

#### **Types of Trees**


1. **Binary Trees:** Each node has up to two children, the left child node and the right child node. This structure is the foundation for more complex tree types like Binary Search Trees and AVL Trees.

2. **Binary Search Trees (BSTs):** A type of Binary Tree where for each node, the left child node has a lower value, and the right child node has a higher value.

3. **AVL Trees:** A type of Binary Search Tree that self-balances so that for every node, the difference in height between the left and right subtrees is at most one. This balance is maintained through rotations when nodes are inserted or deleted.