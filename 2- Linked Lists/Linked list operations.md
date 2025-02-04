
### **Basic things we can do with linked lists are:**

1. Traversal
2. Remove a node
3. Insert a node
4. Sort


---


### **Traversal of a Linked List**

```
class Node {

  constructor(data) {

    this.data = data;

    this.next = null;

  }

}

  

function traverseAndPrint(head) {

  let currentNode = head;

  while (currentNode) {

    console.log(currentNode.data + " -> ");

    currentNode = currentNode.next;

  }

  console.log("null");

}

const node1 = new Node(7);

const node2 = new Node(11);

const node3 = new Node(3);

const node4 = new Node(2);

const node5 = new Node(9);

node1.next = node2;

node2.next = node3;

node3.next = node4;

node4.next = node5;

traverseAndPrint(node1);
```

---

### **lowest value:**

```
class Node {

  constructor(data) {

    this.data = data;

    this.next = null;

  }

}

  

function findLowestValue(head) {

  let minValue = head.data;

  let currentNode = head.next;

  while (currentNode) {

    if (currentNode.data < minValue) {

      minValue = currentNode.data;

    }

    currentNode = currentNode.next;

  }

  return minValue;

}

const node1 = new Node(7);

const node2 = new Node(11);

const node3 = new Node(3);

const node4 = new Node(2);

const node5 = new Node(9);

node1.next = node2;

node2.next = node3;

node3.next = node4;

node4.next = node5;

console.log("The lowest value in the linked list is:", findLowestValue(node1));
```

---

### **Deletes a specific node**

```
class Node {

  constructor(data) {

    this.data = data;

    this.next = null;

  }

}

  

function findLowestValue(head) {

  let minValue = head.data;

  let currentNode = head.next;

  while (currentNode) {

    if (currentNode.data < minValue) {

      minValue = currentNode.data;

    }

    currentNode = currentNode.next;

  }

  return minValue;

}

const node1 = new Node(7);

const node2 = new Node(11);

const node3 = new Node(3);

const node4 = new Node(2);

const node5 = new Node(9);

node1.next = node2;

node2.next = node3;

node3.next = node4;

node4.next = node5;

console.log("The lowest value in the linked list is:", findLowestValue(node1));
```

---

## **Insert Node Position**

```
class Node {

  constructor(data) {

    this.data = data;

    this.next = null;

  }

}

  

function traverseAndPrint(head) {

  let currentNode = head;

  while (currentNode) {

    console.log(currentNode.data + " -> ");

    currentNode = currentNode.next;

  }

  console.log("null");

}

function insertNodeAtPosition(head, newNode, position) {

  if (position === 1) {

    newNode.next = head;

    return newNode;

  }

  let currentNode = head;

  for (let i = 0; i < position - 2; i++) { // this loop iterate until "currentNode" equal the node before position

    if (currentNode === null) {

      break;

    }

    currentNode = currentNode.next;

  }

  newNode.next = currentNode.next;

  currentNode.next = newNode;

  return head;

}

const node1 = new Node(7);

const node2 = new Node(3);

const node3 = new Node(2);

const node4 = new Node(9);

const node5 = new Node(10);

const node6 = new Node(22);

node1.next = node2;

node2.next = node3;

node3.next = node4;

node4.next = node5;

node5.next = node6;

console.log("Original list:");

traverseAndPrint(node1);

// Insert a new node with value 97 at position 2

const newNode = new Node(97);

const updatedHead = insertNodeAtPosition(node1, newNode, 4);

console.log("\nAfter insertion:");

traverseAndPrint(updatedHead);
```

