
> [!NOTE] Info
**A stack is** a data structure that can hold many elements.

---

### **Basic operations we can do on a stack with array are:**

1. **Push**: Adds a new element on the stack.
2. **Pop**: Removes and returns the top element from the stack.
3. **Peek**: Returns the top element on the stack.
4. **isEmpty**: Checks if the stack is empty.
5. **Size**: Finds the number of elements in the stack.


----

### **Implementation with Arrays**

```
// Stack class

class Stack {

  // Array is used to implement stack

  constructor() {

    this.items = [];

  }

  

  // push function

  push(element) {

    // push element into the items

    this.items.push(element);

  }

  // pop function

  pop() {

    // return top most element in the stack

    // and removes it from the stack

    // Underflow if stack is empty

    if (this.items.length == 0) return "Underflow";

    return this.items.pop();

  }

  // peek function

  peek() {

    // return the top most element from the stack

    // but does'nt delete it.

    return this.items[this.items.length - 1];

  }

  // isEmpty function

  isEmpty() {

    // return true if stack is empty

    return this.items.length == 0;

  }

  // printStack function

  printStack() {

    let str = "";

    for (let i = 0; i < this.items.length; i++) str += this.items[i] + " ";

    return str;

  }

}

let stack1 = new Stack();
```

### **Implementation with linked lists**

```
class Node {

  constructor(data) {

    this.data = data;

    this.next = null;

  }

}

  

class Stack {

  constructor() {

    this.top = null;

    this.size = 0;

  }

  push(data) {

    const newNode = new Node(data);

    newNode.next = this.top;

    this.top = newNode;

    this.size++;

  }

  peek() {

    return this.top ? this.top.data : null;

  }

  isEmpty() {

    return this.size === 0;

  }

  pop() {

    if (!this.top) return null;

    const popped = this.top;

    this.top = this.top.next;

    this.size--;

    return popped.data;

  }

}

const stack = new Stack();

stack.push(10);

stack.push(20);

stack.push(30);

console.log(stack);
```

---

## :LiArrowRightCircle: **Go to [[Qeueus]]**
## **:LiArrowRightCircle: Go to [[Complexity#^d28ac9]]**
