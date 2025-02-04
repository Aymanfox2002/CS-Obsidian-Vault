

> [!NOTE] Info
> A **binary search tree (BST)** is a type of binary tree where each node has a value, and it follows these properties:
>
> 1. left subtree lesser than node value 
> 2. Right subtree greater than node value
> 3. Left and right subtree should be **BST** also

```
        3
       /  \
      7    15
     / \   / \
    3   8 14 19
             /
           18
```


---

## **Traversal of a Binary Search Tree**

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
    console.log(node.data + ", ");
    inOrderTraversal(node.right);
}

const root = new TreeNode(13);
const node7 = new TreeNode(7);
const node15 = new TreeNode(15);
const node3 = new TreeNode(3);
const node8 = new TreeNode(8);
const node14 = new TreeNode(14);
const node19 = new TreeNode(19);
const node18 = new TreeNode(18);

root.left = node7;
root.right = node15;

node7.left = node3;
node7.right = node8;

node15.left = node14;
node15.right = node19;

node19.left = node18;

// Traverse
inOrderTraversal(root);
```


---
## **Search for a Value in a BST**

```
function search(node, target) {

  if (node === null) {

      return null;

  } else if (node.data === target) {

      return node;

  } else if (target < node.data) {

      return search(node.left, target);

  } else {

      return search(node.right, target);

  }
}
```



---

## **Insert a Node in a BST**

```
function insert(node, data) {
    if (node === null) {
        return new TreeNode(data);
    } else {
        if (data < node.data) {
            node.left = insert(node.left, data);
        } else if (data > node.data) {
            node.right = insert(node.right, data);
        }
    }
    return node;
}
```


---

## **The Lowest Value in a BST Subtree**

```
function minValueNode(node) {
  let current = node;
  while (current.left !== null) {
      current = current.left;
  }
  return current;
}
```

---

## **Delete a node in a BST**


> [!info] How it works
> 1. If the node is a leaf node, remove it by removing the link to it.
> 2. If the node only has one child node, connect the parent node of the node you want to remove to that child node.
> 3. If the node has both right and left child nodes: Find the node's in-order successor, change values with that node, then delete it.




```
function deleteNode(node, data) {

    if (!node) {

        return null;

    }

  

    if (data < node.data) {

        node.left = deleteNode(node.left, data);

    } else if (data > node.data) {

        node.right = deleteNode(node.right, data);

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

        node.data = minValueNode(node.right).data;

        node.right = deleteNode(node.right, node.data);

    }

  

    return node;

}

  
  

function minValueNode(node) {

    let current = node;

    while (current.left !== null) {

        current = current.left;

    }

    return current;

}
```

---

## **BST Compared to Other Data Structures**

> Binary Search Trees take the best from two other data structures: Arrays and Linked Lists.

| Data Structure     | Searching for a value               | Delete / Insert leads to shifting in memory |
| ------------------ | ----------------------------------- | ------------------------------------------- |
| Sorted Array       | <mark class="hltr-g">O(logn)</mark> | <mark class="hltr-r">Yes</mark>             |
| Linked List        | <mark class="hltr-r">O(n)</mark>    | **<mark class="hltr-g">No</mark>**          |
| Binary Search Tree | <mark class="hltr-g">O(logn)</mark> | **<mark class="hltr-g">No</mark>**          |

---

## **Balanced BST VS Unbalanced BST**


```
        13
       /  \
      7    15
     / \   / \
    3   8 14 19
              /
             18
```

```
        7
      /  \
     3    13
         / \
        8   19
             \
             15
               \
               18
```


> [!warning] Complexity
> The **time complexity** for searching a BST for a value is O(h), where **h** is the height of the tree.
> For a BST with most nodes on the bottom side for example, the height of the tree becomes larger than it needs to be, and the worst case search will take longer. Such trees are called unbalanced.
> 
> Both Binary Search Trees above have the same nodes, and in-order traversal of both trees gives us the same result but the height is very different. It takes longer time to search the unbalanced tree above because it is higher.

---

## **:LiArrowRightCircle: Go to [[AVL Trees]]**

