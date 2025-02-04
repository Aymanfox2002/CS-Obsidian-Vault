
> [!NOTE] Title
> **“Algorithmic Complexity”** refers to the computing resources needed by an algorithm to solve a problem. These computing resources can be the time taken for program execution **(time complexity)**, or the space used in memory during its execution **(space complexity)**. The aim is to minimize these resources, so an algorithm that takes less time and space is considered more efficient. Complexity is usually expressed using **Big O** notation, which describes the upper bound of time or space needs, and explains how they grow in relation to the input size. It’s important to analyze and understand the algorithmic complexity to choose or design the most efficient algorithm for a specific use-case.

---

### **Time Complexity Analysis** 

>**"What factors affect algorithm time?"**

1. Single processor / Multi-processor
2. Core Speed
3. 32 / 64 Bit
4. Read / write Ram
5. Programing language
6. Compiler
7. input



>What is mean **"Frequency Count Method"**?

**The frequency count method** is a simple and effective way to analyze and measure the efficiency of algorithms by counting how many times each operation or step in the code is executed. This method helps understand the time complexity of an algorithm in terms of how the running time grows with input size.



> **Identify the Basic Operations:**

Basic operations are the individual actions that the algorithm performs, like:

- Arithmetic operation       **<mark class="hltr-r">1 unit of time</mark>**
- Assignment operation     **<mark class="hltr-r">1 unit of time</mark>**
- Comparison                     **<mark class="hltr-r">1 unit of time</mark>**
- Return Statement             **<mark class="hltr-r">1 unit of time</mark>**




> [!important] **Count the Frequency of Each Operation**
> For each part of the algorithm, you count how many times that specific operation is executed for a given input size **_n_** .

---

### Example 1

```
function sumArray(arr) {

  let sum = 0;               // 1 operation

  for (let i = 0; i < arr.length; i++) {   // (n + 1) operations (n comparisons + 1 final check)

      sum += arr[i];         // n operations (1 for each element in the array)

  }

  return sum;                // 1 operation

}
```

Total operations: 1 + (n + 1) + n + 1 = **2n + 3**  => **n**

### Example 2

```
let i = 1;

let n = 10;

while (i < n) {

  i *= 2;

}
```

> **Finding the Number of Iterations:**

	- After the first iteration: i = 2^1
	- After the second iteration: i = 2^2
	- After the k-th iteration: i = 2^k 

We want to find k such that 2^k >= n. Taking the logarithm base 2 on both sides: 

$K = log(2)n$

---
#### **Time complexity & Space complexity**

^d28ac9


![[Array Sorting Algorithms.jpg]] ^8f4f05


![[Common Data Structure Operations-2.jpg]]


![[Common Data Structure Operations.jpg]]

---
## **:LiArrowRightCircle: Go to [[Asymptotic Notation]]**
