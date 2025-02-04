
> [!info] Info
> - Asymptotic Notation is a mathematical concept used to describe the behavior of functions, especially the time complexity of algorithms, as the input size grows larger. It helps us understand how efficient an algorithm is when dealing with large amounts of data by focusing on the  **growth rate** of the algorithm's runtime or space requirements.
> 
> - Asymptotic Notation is essential in computer science because it abstracts away the specific details of the machine or programming language and focuses on how algorithms perform relative to the size of the input.


---

### **Key Types of Asymptotic Notation:**

1. Big O Notation (O) — Upper Bound  **(<mark class="hltr-r">worst case</mark>)**

2. Omega Notation (Ω) — Lower Bound

3. Theta Notation (Θ) — Tight Bound

4. Little o Notation (o) — Upper Bound (Loose)

5. Little Omega Notation (ω) — Lower Bound (Loose)


> [!warning] Note
> Developers focus on Big O Notation because it describes the worst-case scenario, which is crucial for ensuring the algorithm performs efficiently even under maximum load.


---

### **Big O Notation**

**Big O notation** describes the worst-case scenario for an algorithm. It gives an upper bound on the time or space complexity as the input size, denoted by  **n** , increases.

**Definition**: f(n) = O(g(n)) means that the function f(n) does not grow faster than g(n) for large values of n. In simpler terms, f(n) is bounded above by g(n).

**Example**: Suppose you have a function f(n) = 3n^2 + 5n + 2. As n grows large, the term 3n^2 dominates, so the time complexity is **O(n^2)**.

**Usage**: **Big O** is used to measure the efficiency of an algorithm, particularly how long it takes to run in the worst-case scenario.

---

### **Common Big O Time Complexities:**

![[Big-O Complexity Chart.jpg]]


---

### **Rate of grows**

![[Common Data Structure Operations.jpg]]

---

### **Examples of Big O cases**

>**EX** **1: Simple Nested Loop (Multiplying Outer and Inner Loops)**

```
for (let i = 0; i < n; i++) {     // Outer loop runs n times

  for (let j = 0; j < n; j++) {   // Inner loop runs n times for each i

    console.log(i, j);

  }

}
```

#### Time Complexity Analysis:

· Outer loop: Runs n times.

· Inner loop: Runs n times for each iteration of the outer loop.

Total time complexity: O(n)×O(n) = **<mark class="hltr-g">O(n^2</mark>)**



>**EX****2: Nested Loop with Changing Inner Bound (Sum of Series)**

```
for (let i = 0; i < n; i++) {     // Outer loop runs n times

  for (let j = 0; j < i; j++) {   // Inner loop runs i times for each i

    console.log(i, j);

  }

}
```

#### **Time Complexity Analysis:**

**Outer loop:** Runs n times.
**Inner loop:** Runs 0 times when I = 0, 1 time when i=1, 2 times when i=2, and so on until n−1.

	The total number of iterations is the sum of the series: 0+1+2+...(n-1) = n(n-1) / 2

**Total time complexity**: n^2 - n / 2 we simplify to **<mark class="hltr-g">O(n^2</mark>)**


> **EX3: Loop with Constant Inner Work (Multiplying Outer and Constant Work)**

```
for (let i = 0; i < n; i++) {     // Outer loop runs n times

  // Inner loop or constant work

  console.log("Constant work");

}
```

#### **Time Complexity Analysis**

- **Outer loop:** Runs n times
- **Inner loop/constant work**: Does not depend on n; it runs a constant amount of work (O(1)) per iteration of the outer loop.

**Total time complexity:** O(n)×O(1) = **<mark class="hltr-g">O(n</mark>)**



> **EX4: Reducing Input Size in the Inner Loop (Logarithmic Inner Loop)**

```
for (let i = 0; i < n; i++) {      // Outer loop runs n times

  let j = 1;

  while (j < n) {                  // Inner loop runs log(n) times

    console.log(i, j);

    j *= 2;                        // j doubles each iteration

  }

}
```

#### **Time Complexity Analysis:**

- **Outer loop**: Runs n times.
- **Inner loop**: The variable j doubles each time, so it runs O(log n) times.

**Total time complexity:** O(n)×O(logn) = **<mark class="hltr-g">O(nlogn</mark>)**



> **EX****5: Triple Nested Loop (Multiplying All Three Loops)**

```
for (let i = 0; i < n; i++) {         // Outer loop runs n times

  for (let j = 0; j < n; j++) {       // Middle loop runs n times for each i

    for (let k = 0; k < n; k++) {     // Inner loop runs n times for each j

      console.log(i, j, k);

    }

  }

}
```

#### **Time Complexity Analysis:**

- **Outer loop:** Runs **n** times.
- **Middle loop:** Runs **n** times for each iteration of the outer loop.
- **Inner loop:** Runs **n** times for each iteration of the middle loop.

Total time complexity: O(n)×O(n)×O(n) = **<mark class="hltr-g">O(n3</mark>)**

---

### **Specific Examples**


>**O(log n) - Logarithmic Time Complexity:**

```
let n = 16;

while (n > 1) {

  // Some constant work here

  n = Math.floor(n / 2); // n is halved in each iteration

}
```

##### **First Step: Find the Pattern**

	 n = 16
	 Iteration 1: n = 8  (16/2)
	 Iteration 2: n = 4  (8/2)
	 Iteration 3: n = 2  (4/2)
	 Iteration 4: n = 1  (2/2) (loop stops

##### **Second Step: Find the Stopping Condition**

- Loop runs while n > 1
- In each step, n is divided by 2
- We're looking for how many times we divide n by 2 to get to 

##### **Third Step: Write Mathematical Pattern**

 - Starting value: n
 - After k steps: n/(2^k)
 - When loop stops: n/(2^k) = 1
 - Therefore: n = 2^k
 - Solve for k: k = log₂(n)


##### **Final Step: Big O Notation**

- Number of iterations = log₂(n)
- Therefore, time complexity is **<mark class="hltr-g">O(log n</mark>)**



>**O(√n) - Square Root Time Complexity:**

```
let i = 1;

let n = 100;

while (i * i < n) {

  // Some constant work here

  i++;

}
```


##### **First, let's understand what's happening:**

- We start with i = 1
- We increment i by 1 each iteration
- The loop continues while i² < n

##### **The key is to find when the loop stops:**

- The loop stops when i² ≥ n
- In other words, when i ≥ √n

##### **Therefore:**

- The loop starts at i = 1
- Ends when i reaches ceiling(√n)
- Increments by 1 each time

#####  **Number of iterations:**

- The loop will iterate ceiling(√n) - 1 times

##### **Time Complexity:**

- The time complexity is O(√n)

##### **For your specific example where n = 100:**

- The loop will stop when i reaches 10 (since 10² = 100)
- It will iterate 9 times (from i = 1 to i = 9)



> [!success] Result
> So while this might look like it could be O(n) at first glance, it's actually **O(√n)**, which is more efficient. The reason is that we're checking i² against n, not i against n.
