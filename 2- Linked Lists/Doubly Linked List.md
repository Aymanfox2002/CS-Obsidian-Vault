![[doubly linked list.png]]

---

## **Implementation**

```
class Node {

  constructor(data) {

    this.data = data;

    this.next = null;

    this.prev = null;

  }

}

  

const node1 = new Node(3);

const node2 = new Node(5);

const node3 = new Node(13);

const node4 = new Node(2);

// Setting up next and prev links

node1.next = node2;

node2.prev = node1;

node2.next = node3;

node3.prev = node2;

node3.next = node4;

node4.prev = node3;

console.log(node2);

// Traversing forward

console.log("\nTraversing forward:");

let currentNode = node1;

while (currentNode) {

  console.log(currentNode.data + " -> "); // You can use console.log instead for browsers

  currentNode = currentNode.next;

}

// Traversing backward

console.log("\nTraversing backward:");

currentNode = node4;

while (currentNode) {

  console.log(currentNode.data + " -> "); // You can use console.log instead for browsers

  currentNode = currentNode.prev;

}
```

---

## **:LiArrowRightCircle: Go to [[Circular singly linked list]]**
