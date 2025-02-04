

![[doubly_circular_linked_list.png]]


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

  

// Setting up the doubly circular linked list

node1.next = node2;

node1.prev = node4;

node2.prev = node1;

node2.next = node3;

node3.prev = node2;

node3.next = node4;

node4.prev = node3;

node4.next = node1;

  

// Traversing forward

console.log("\nTraversing forward:");

let currentNode = node1;

const startNode = node1;

console.log(currentNode.data + " -> ");

currentNode = currentNode.next;

while (currentNode !== startNode) {

  console.log(currentNode.data + " -> ");

  currentNode = currentNode.next;

}

console.log("...");

  

// Traversing backward

console.log("\nTraversing backward:");

currentNode = node4;

const endNode = node4;

console.log(currentNode.data + " -> ");

currentNode = currentNode.prev;

while (currentNode !== endNode) {

  console.log(currentNode.data + " -> ");

  currentNode = currentNode.prev;

}

console.log("...");
```

---

## **:LiArrowRightCircle: Go to [[Linked list operations]] **
