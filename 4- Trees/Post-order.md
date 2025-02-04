
> [!NOTE] Info
> **Post-order** Traversal is a type of Depth First Search, where each node is visited in a certain order.

## Tree Looks

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

## **Implementation**

```
class TreeNode {

    constructor(data) {

        this.data = data;

        this.left = null;

        this.right = null;

    }

}

function inOrderTraversal(node) {

    if (node === null) {
        return;
    }

    inOrderTraversal(node.left);
    inOrderTraversal(node.right);
    console.log(node.data + ", ");
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

  

// Traverse

inOrderTraversal(root);
```

