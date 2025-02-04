
> [!info] Info
> **Radix Sort** is a non-comparative sorting algorithm that sorts numbers by processing individual digits. The idea is to sort the numbers digit by digit, starting from the least significant digit (LSD) to the most significant digit (MSD). This process is repeated for each digit position until the entire list is sorted.


---

## **How It Works**

1. **Determine the Maximum Value:** First, find the maximum number in the array to determine the number of digits in the largest number. This helps to know how many iterations are needed.

2. **Initialize Buckets:** Create an array of 10 empty buckets (or sub-arrays), one for each digit (0 through 9).

3. **Sort by Each Digit:**

 - Start with the least significant digit (e.g., the ones place).

 - Place each number in the corresponding bucket based on the current digit being examined.

 - Reconstruct the array by collecting numbers from the buckets in order.

 - Move to the next significant digit (e.g., tens place) and repeat the process.

4. **Repeat:** Continue sorting by the next significant digit until all digits have been processed.

5. **Final Sorted Array:** After processing all digits, the array will be fully sorted.

---

## **Implementation**

```
let myArray = [170, 45, 75, 90, 802, 24, 2, 66];

console.log("Original array:", myArray);

let radixArray = [[], [], [], [], [], [], [], [], [], []];

let maxVal = Math.max(...myArray);

let exp = 1;

while (Math.floor(maxVal / exp) > 0) {

  while (myArray.length > 0) {

    let val = myArray.pop();

    let radixIndex = Math.floor(val / exp) % 10; //take last number

    radixArray[radixIndex].push(val);

  }

  for (let bucket of radixArray) {

    while (bucket.length > 0) {

      let val = bucket.pop();

      myArray.push(val);

    }

  }

  exp *= 10;

}

console.log("Sorted array:", myArray);
```

---

## **:LiArrowRightCircle: Go to [[Merge sort]]**

