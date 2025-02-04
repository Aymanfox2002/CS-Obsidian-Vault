

> [!NOTE] Info
> **A queue is** a data structure that can hold many elements.


> [!warning] Queues VS Stacks
> **A stack** follows the Last In, First Out (LIFO) principle, where the last element added is the first to be removed.
>  **A queue** follows the First In, First Out (FIFO) principle, where the first element added is the first to be removed.
>   Think of a stack as a stack of plates and a queue as a line of people waiting for a bus.

---

### **Implementation with arrays**

```
let queue = [];

  

queue.push("A");

queue.push("B");

queue.push("C");

console.log("Queue: ", queue);

// Removes the first element

let element = queue.shift();

console.log("queue: ", element);

// Peek

let frontElement = queue[0];

console.log("Peek: ", frontElement);

// isEmpty

let isEmpty = queue.length === 0;

console.log("isEmpty: ", isEmpty);

// Size

console.log("Size: ", queue.length);
```


### **Implementation with linked lists**


```
class Node {

  constructor(value) {

    this.value = value;

    this.next = null;

  }

}

  

class Queue {

  constructor() {

    this.first = null;

    this.last = null;

    this.size = 0;

  }

  isEmpty() {

    return !this.size;

  }

  enqueue(item) {

    // Create node

    const newNode = new Node(item);

    if (this.isEmpty()) {

      this.first = newNode;

      this.last = newNode;

    } else {

      this.last.next = newNode;

      this.last = newNode;

    }

    this.size++;

    return this;

  }

  dequeue() {

    //* if our queue is empty we return null

    if (this.isEmpty()) return null;

    const itemToBeRemoved = this.first;

    /**

    ** if both our first and last node are pointing the same item

    ** we dequeued our last node.

    */

    if (this.first === this.last) {

      this.last = null;

    }

    this.first = this.first.next;

    this.size--;

    return itemToBeRemoved;

  }

  /**

  * * Returns the next element to be dequeued.

  */

  peek() {

    return this.first;

  }

}

const queue = new Queue();

queue.enqueue(10);

queue.enqueue(20);

queue.enqueue(30);

queue.enqueue(40);

console.log(queue);
```

---
