
![[singly linked list.png]]

---

## **Implementation**

```
class Node {

  constructor(data) {

    this.data = data;

    this.next = null;

  }

}

  

const node1 = new Node(3);

const node2 = new Node(5);

const node3 = new Node(13);

const node4 = new Node(2);

  
  

// Creating the circular linked list

node1.next = node2;

node2.next = node3;

node3.next = node4;

node4.next = node1; // Makes it circular by pointing the last node to the first node

  
  

// Traversing the list in a circular manner

let currentNode = node1;

const startNode = node1;

console.log(currentNode.data + " -> ");

currentNode = currentNode.next;

while (currentNode !== startNode) {

  console.log(currentNode.data + " -> ");

  currentNode = currentNode.next;

}
```

---

## **:LiArrowRightCircle: Go to [[Doubly circular linked list]] **
