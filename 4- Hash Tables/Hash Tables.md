
> [!NOTE] Info
> - A **Hash Table** is a data structure designed for fast data operations, enabling quick searching, adding, and deleting of elements even with large datasets.
> -  Compared to linked lists and arrays, hash tables significantly speed up lookups by using a hash function to directly access stored data.


---

### **Implementation**

```
class HashTable {

  constructor() {

    this.table = new Array(127);

    this.size = 0;

  }

  _hash(key) {

    let hash = 0;

    for (let i = 0; i < key.length; i++) {

      hash += key.charCodeAt(i);

    }

    return hash % this.table.length;

  }

  

  set(key, value) {

    const index = this._hash(key);

    if (this.table[index]) {

      for (let i = 0; i < this.table[index].length; i++) {

        // Find the key/value pair in the chain

        if (this.table[index][i][0] === key) {

          this.table[index][i][1] = value;

          return;

        }

      }

      // not found, push a new key/value pair

      this.table[index].push([key, value]);

    } else {

      this.table[index] = [];

      this.table[index].push([key, value]);

    }

    this.size++;

  }

  

  get(key) {

    const target = this._hash(key);

    if (this.table[target]) {

      for (let i = 0; i < this.table[target].length; i++) {

        if (this.table[target][i][0] === key) {

          return this.table[target][i][1];

        }

      }

    }

    return undefined;

  }

  remove(key) {

    const index = this._hash(key);

    if (this.table[index] && this.table[index].length) {

      for (let i = 0; i < this.table[index].length; i++) {

        if (this.table[index][i][0] === key) {

          this.table[index].splice(i, 1);

          this.size--;

          return true;

        }

      }

    } else {

      return false;

    }

  }

  display() {

    this.table.forEach((values, index) => {

      const chainedValues = values.map(

        ([key, value]) => `[ ${key}: ${value} ]`

      );

      console.log(`${index}: ${chainedValues}`);

    });

  }

}
```

---


> [!question] Note
> A Map is a built-in JavaScript object that also stores key-value pairs, but it maintains the insertion order and allows any data type as a key.

---

### **:LiTimer: [[Complexity#^d28ac9]]**
