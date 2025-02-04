
> [!info] Info
> In-order Traversal is a type of Depth First Search, where each node is visited in a certain order.

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

    console.log(node.data + ", ");

    inOrderTraversal(node.right);

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

---

## **how to perform tree traversals on the array-implemented binary tree?**

```
const binary_tree_array = ['R', 'A', 'B', 'C', 'D', 'E', 'F', null, null, null, null, null, null, 'G'];

  

function left_child_index(index) {

    return 2 * index + 1;

}

  

function right_child_index(index) {

    return 2 * index + 2;

}

  

function pre_order(index) {

    if (index >= binary_tree_array.length || binary_tree_array[index] === null) {

        return [];

    }

    return [binary_tree_array[index]].concat(pre_order(left_child_index(index))).concat(pre_order(right_child_index(index)));

}

  

function in_order(index) {

    if (index >= binary_tree_array.length || binary_tree_array[index] === null) {

        return [];

    }

    return in_order(left_child_index(index)).concat([binary_tree_array[index]]).concat(in_order(right_child_index(index)));

}

  

function post_order(index) {

    if (index >= binary_tree_array.length || binary_tree_array[index] === null) {

        return [];

    }

    return post_order(left_child_index(index)).concat(post_order(right_child_index(index))).concat([binary_tree_array[index]]);

}

  

console.log("Pre-order Traversal:", pre_order(0));

console.log("In-order Traversal:", in_order(0));

console.log("Post-order Traversal:", post_order(0));
```