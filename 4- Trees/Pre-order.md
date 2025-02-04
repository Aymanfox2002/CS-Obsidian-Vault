

> [!info] Info
> **Pre-order Traversal** is a type of Depth First Search, where each node is visited in a certain order.
> 
> **Pre-order Traversal** is done by visiting the root node first, then recursively do a pre-order traversal of the left subtree, followed by a recursive **pre-order traversal** of the right subtree. It's used for creating a copy of the tree, prefix notation of an expression tree, etc.
> 
> This traversal is **"pre"** order because the node is visited **"before"** the recursive pre-order traversal of the left and right subtrees.

## **Tree Looks**

```
        R
       / \
      A   B
     / \ / \
    C  D E  F
           /
          G
```

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

  

function preOrderTraversal(node) {

  if (node === null) {

    return;

  }

  console.log(node.data + ", ");

  preOrderTraversal(node.left);

  preOrderTraversal(node.right);

}

  

const root = new TreeNode("R");

const nodeA = new TreeNode("A");

const nodeB = new TreeNode("B");

const nodeC = new TreeNode("C");

const nodeD = new TreeNode("D");

const nodeE = new TreeNode("E");

const nodeF = new TreeNode("F");

const nodeG = new TreeNode("G");

  

root.left = nodeA;

root.right = nodeB;

  

nodeA.left = nodeC;

nodeA.right = nodeD;

  

nodeB.left = nodeE;

nodeB.right = nodeF;

  

nodeF.left = nodeG;

  

// Traverse

preOrderTraversal(root);
```


