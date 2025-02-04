

> [!info] Info
> **A Binary Tree** is a type of tree data structure where each node can have a maximum of two child nodes


This limitations, that a node can have a maximum of two child nodes, gives us many benefits:

- Algorithms like traversing, searching, insertion and deletion become easier to understand, to implement, and run faster.
- Keeping data sorted in a Binary Search Tree (BST) makes searching very efficient.
- Balancing trees is easier to do with a limited number of child nodes, using an AVL Binary Tree for example.
- Binary Trees can be represented as arrays, making the tree more memory efficient.

---


### **Binary Trees vs Arrays and Linked Lists**

- **Arrays** are fast when you want to access an element directly, like element number 700 in an array of 1000 elements for example. But inserting and deleting elements require other elements to shift in memory to make place for the new element, or to take the deleted elements place, and that is time consuming.
- **Linked Lists** are fast when inserting or deleting nodes, no memory shifting needed, but to access an element inside the list, the list must be traversed, and that takes time.
- **Binary Trees**, such as Binary Search Trees and AVL Trees, are great compared to Arrays and Linked Lists because they are BOTH fast at accessing a node, AND fast when it comes to deleting or inserting a node, with no shifts in memory needed.

We will take a closer look at how Binary Search Trees (BSTs) and AVL Trees work on the next two pages, but first let's look at how a Binary Tree can be implemented, and how it can be traversed.

---

### **Types of Binary Trees**


There are different variants, or types, of Binary Trees worth discussing to get a better understanding of how Binary Trees can be structured.

#### **Balanced binary tree**

the height difference between the left and right subtrees of any node is at most 1

```
        A
       / \
      B   C
     / \   \
    D   E   F

```

```
        1
       / \
      2   3
     / \ / \
    4  5 6  7

```

```
        1
       / \
      2   3
     / 
    4   

```

#### **Non balanced binary tree**

```
        1
       /
      2
     /
    3
   /
  4
```

```
        1
         \
          2
           \
            3
             \
              4
```

```
        1
       / \
      2   3
     /
    4
   /
  5
```


#### **Full or Strictly binary tree**

A binary tree is full if every node has 0 or 2 children

![[full binary tree.png]]

#### **Complete binary tree**

1. All levels is completely filled excepted the last level
2. All nodes as left as possible in last level

![[Complete binary tree.png]]

#### **perfect binary tree**

All levels in completely filled

![[perfect binary tree.png]]


---
### **Binary trees laws**

#### **The number of edges**
**<mark class="hltr-g">nodes - 1</mark>** 
#### **The maximum numbers of nodes at binary tree on specific level**
<mark class="hltr-g">$2^L$</mark>  
**L:** the node's level

#### **Maximum number of nodes in a binary tree**
<mark class="hltr-g">2^(H+1) - 1</mark>
**H:** the tree height
#### **the minimum height in binary tree**
<mark class="hltr-g">(log2 (n+1)) - 1</mark>

---

### **Implementation**

```
class TreeNode {

    constructor(data) {

        this.data = data;

        this.left = null;

        this.right = null;

    }

}

  

const root = new TreeNode('R');

const nodeA = new TreeNode('A');

const nodeB = new TreeNode('B');

const nodeC = new TreeNode('C');

const nodeD = new TreeNode('D');

const nodeE = new TreeNode('E');

const nodeF = new TreeNode('F');

const nodeG = new TreeNode('G');

  

root.left = nodeA;

root.right = nodeB;

  

nodeA.left = nodeC;

nodeA.right = nodeD;

  

nodeB.left = nodeE;

nodeB.right = nodeF;

  

nodeF.left = nodeG;

  

// Test

console.log("root.right.left.data:", root.right.left.data);
```


Going through a Tree by visiting every node, one node at a time, is called **traversal**.

There are two main categories of Tree traversal methods:

1. **Breadth First Search (BFS)** is when the nodes on the same level are visited before going to the next level in the tree. This means that the tree is explored in a more sideways direction.

2. **Depth First Search (DFS)** is when the traversal moves down the tree all the way to the leaf nodes, exploring the tree branch by branch in a downwards direction.

There are three different types of DFS traversals:

- [[Pre-order]]
- [[In-order]]
- [[Post-order]]

---

## **:LiArrowRightCircle: Go to [[Array Implementation of Binary Trees]]**
