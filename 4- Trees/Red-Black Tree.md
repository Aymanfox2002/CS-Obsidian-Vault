

![[Red-Black Tree 1.png]]







> [!info] Info
> A Red-Black Tree is a self-balancing binary search tree where each node contains an extra bit for denoting the color (either red or black). It ensures that the tree remains approximately balanced, with operations like insertion, deletion, and search taking O(log n) time. The tree maintains several properties to enforce balance, such as no two consecutive red nodes and equal black heights for all paths from a node to its descendant leaves.



----

### **Properties of Red-Black Trees**

1. **Node Color**: Each node is either red or **black**.
2. **Root Property**: The root of the tree is always **black**.
3. **Red Property**: Red nodes cannot have red children (no two consecutive red nodes on any path).
4. **Black Property**: Every path from a node to its descendant null nodes (leaves) has the same number of **black** nodes.
5. **Leaf Property**: All leaves (NIL nodes) are **black**.

>These properties ensure that the longest path from the root to any leaf is no more than twice as long as the shortest path, maintaining the tree’s balance and efficient performance.

![[examples-of-red-black-tree-22.webp]]

- The **Correct Red-Black Tree** in above image ensures that every path from the root to a leaf node has the same number of black nodes. In this case,​ there is one (excluding the root node).

- The **Incorrect Red Black Tree** does not follow the red-black properties as ****two red nodes**** are adjacent to each other. Another problem is that one of the paths to a leaf node has zero black nodes, whereas the other two contain a black node.


---

## **Why Red-Black Trees?**

Most Binary Search Tree (BST) operations have a time complexity of O(h), where h is the height of the tree. For skewed trees, this can degrade to O(n). Ensuring the tree height remains O(log n) after insertions and deletions guarantees an upper bound of O(log n) for operations. Red-Black Trees achieve this by maintaining their height at O(log n), regardless of the number of nodes.

|Sr. No.|Algorithm|Time Complexity|
|---|---|---|
|1.|Search|O(log n)|
|2.|Insert|O(log n)|
|3.|Delete|O(log n)|

---

## **Comparison with** **[[AVL Trees]]**

**Both AVL (Adelson-Velsky and Landis) and Red-Black Trees are self-balancing binary search trees, but they have different balancing methods and properties. Let's compare them:**


| **Property**             | **Red-Black Tree**                    | **AVL Tree**                          |
| :----------------------- | :------------------------------------ | :------------------------------------ |
| **Balancing Method**     | Color Balance (Less Strict)           | Height Balance (Strict)               |
| **Tree Height**          | **O(log n)**                          | Closer to **O(log n)**                |
| **Rotations**            | Fewer                                 | More frequent                         |
| **Insertion Complexity** | **O(log n)** with fewer rotations     | **O(log n)** with more rotations      |
| **Deletion Complexity**  | **O(log n)** with simpler rebalancing | **O(log n)** with complex rebalancing |
| **Ideal Use Cases**      | General-Purpose, Operating Systems    | Read-Intensive, Database Indexing     |

---
## **Interesting points about Red-Black Tree:**

- The **black** height of the red-black tree is the number of black nodes on a path from the root node to a leaf node. Leaf nodes are also counted as ****black**** nodes. So, a red-black tree of height ****h**** has ****black height >= h/2****.
- Height of a red-black tree with ****n**** nodes is $h<= 2 * log2(n + 1)$
- All leaves (NIL) are ****black****.
- The ****black**** depth of a node is defined as the number of black nodes from the root to that node i.e the number of black ancestors.