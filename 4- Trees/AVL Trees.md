

> [!info] Info
> The **AVL** Tree is a type of Binary Search Tree named after two Soviet inventors Georgy **A**delson-**V**elsky and Evgenii **L**andis who invented the AVL Tree in 1962.
> 
> AVL trees are self-balancing, which means that the tree height is kept to a minimum so that a very fast runtime is guaranteed for searching, inserting and deleting nodes, with time complexity **O(log⁡n)**.

The only difference between a regular [[Binary search tree]] and an AVL Tree is that AVL Trees do rotation operations in addition, to keep the tree balance.

A Binary Search Tree is in balance when the difference in height between left and right subtrees is less than 2.

By keeping balance, the AVL Tree ensures a minimum tree height, which means that search, insert, and delete operations can be done really fast.

---

## **Implementation**

```
class Node {

    constructor(data) {

        this.data = data;

        this.left = null;

        this.right = null;

        this.height = 1; // New nodes always start with a height of 1.

    }

}

  

class AVLTree {

    constructor() {

        this.root = null;

    }

  

    // Utility function to get the height of a node.

    getHeight(node) {

        return node ? node.height : 0;

    }

  

    // Utility function to get balance factor of a node.

    getBalanceFactor(node) {

        return this.getHeight(node.left) - this.getHeight(node.right);

    }

  

    // Rotate node to the right.

    rightRotate(y) {

        const x = y.left;

        const T3 = x.right;

  

        // Perform rotation

        x.right = y;

        y.left = T3;

  

        // Update heights post rotation

        y.height = Math.max(this.getHeight(y.left), this.getHeight(y.right)) + 1;

        x.height = Math.max(this.getHeight(x.left), this.getHeight(x.right)) + 1;

  

        return x; // New root

    }

  

    // Rotate node to the left.

    leftRotate(x) {

        const y = x.right;

        const T2 = y.left;

  

        // Perform rotation

        y.left = x;

        x.right = T2;

  

        // Update heights post rotation

        x.height = Math.max(this.getHeight(x.left), this.getHeight(x.right)) + 1;

        y.height = Math.max(this.getHeight(y.left), this.getHeight(y.right)) + 1;

  

        return y; // New root

    }

  

    // Recursively inserts a node and performs rotations if necessary.

    insert(node, data) {

        if (!node) return new Node(data);

  

        if (data < node.data) {

            node.left = this.insert(node.left, data);

        } else if (data > node.data) {

            node.right = this.insert(node.right, data);

        } else {

            return node; // Duplicate data not allowed.

        }

  

        // Update node's height.

        node.height = 1 + Math.max(this.getHeight(node.left), this.getHeight(node.right));

  

        // Get the balance to check if it became unbalanced.

        const balance = this.getBalanceFactor(node);

  

        // Left heavy scenario

        if (balance > 1) {

            if (data < node.left.data) {

                return this.rightRotate(node);

            } else {

                node.left = this.leftRotate(node.left);

                return this.rightRotate(node);

            }

        }

  

        // Right heavy scenario

        if (balance < -1) {

            if (data > node.right.data) {

                return this.leftRotate(node);

            } else {

                node.right = this.rightRotate(node.right);

                return this.leftRotate(node);

            }

        }

  

        return node;

    }

  

    add(data) {

        this.root = this.insert(this.root, data);

    }

  

    // Utility function to find the node with the minimum value.

    minValueNode(node) {

        let current = node;

        while (current.left !== null) {

            current = current.left;

        }

        return current;

    }

  

    // Recursively deletes a node and performs rotations if necessary.

    delete(node, data) {

        if (!node) return node;

  

        if (data < node.data) {

            node.left = this.delete(node.left, data);

        } else if (data > node.data) {

            node.right = this.delete(node.right, data);

        } else {

            // Node with only one child or no child

            if (!node.left) {

                let temp = node.right;

                node = null;

                return temp;

            } else if (!node.right) {

                let temp = node.left;

                node = null;

                return temp;

            }

  

            // Node with two children, get the in-order successor

            let temp = this.minValueNode(node.right);

            node.data = temp.data;

            node.right = this.delete(node.right, temp.data);

        }

  

        if (!node) return node;

  

        // Update node's height.

        node.height = 1 + Math.max(this.getHeight(node.left), this.getHeight(node.right));

  

        // Get the balance to check if it became unbalanced.

        const balance = this.getBalanceFactor(node);

  

        // Left heavy scenario

        if (balance > 1) {

            if (this.getBalanceFactor(node.left) >= 0) {

                return this.rightRotate(node);

            } else {

                node.left = this.leftRotate(node.left);

                return this.rightRotate(node);

            }

        }

  

        // Right heavy scenario

        if (balance < -1) {

            if (this.getBalanceFactor(node.right) <= 0) {

                return this.leftRotate(node);

            } else {

                node.right = this.rightRotate(node.right);

                return this.leftRotate(node);

            }

        }

  

        return node;

    }

  

    remove(data) {

        this.root = this.delete(this.root, data);

    }

}

let theTree = new AVLTree()

theTree.add(10)

theTree.add(30)

theTree.add(20)

theTree.add(10)

console.log(theTree)
```