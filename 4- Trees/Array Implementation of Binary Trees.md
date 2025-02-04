



## **Pointer vs. Array Implementation**

  Binary Trees are often implemented with pointers, especially when frequently modified. However, for read-heavy operations, an array implementation can be more efficient.


## **Memory Efficiency**

Arrays use less memory and can be easier to implement.


## **Cache Locality**

Arrays benefit from cache locality, where recently accessed memory or nearby memory is stored in the fast cache, making subsequent accesses faster.


## **Contiguous Storage**

 Array elements are stored contiguously, enhancing performance as the next element is likely already cached.


> [!warning] Note
> This approach is particularly beneficial for perfect or nearly perfect binary trees, where every internal node has exactly two children, and all leaf nodes are at the same level

---

 So if we have this tree:
```
        R
       / \
      A   B
     / \ / \
    C  D E  F
           /
          G
```

first thing we convert it into this array: 

```
const binary_tree_array = ['R', 'A', 'B', 'C', 'D', 'E', 'F', null, null, null, null, null, null, 'G'];
```


Below is an Array implementation of the Binary Tree,

```
const binary_tree_array = ['R', 'A', 'B', 'C', 'D', 'E', 'F', null, null, null, null, null, null, 'G'];

function left_child_index(index) {
    return 2 * index + 1;
}

function right_child_index(index) {

    return 2 * index + 2;

}

function get_data(index) {
    if (index >= 0 && index < binary_tree_array.length) {
        return binary_tree_array[index];
    }
    return null;
}

  

const right_child = right_child_index(0);

const left_child_of_right_child = left_child_index(right_child);

const data = get_data(left_child_of_right_child);

  

console.log("root.right.left.data:", data);
```

---

## **:LiArrowRightCircle: Go to [[Binary search tree]]**
