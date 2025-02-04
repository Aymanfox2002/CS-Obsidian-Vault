

> [!info] Info
> Binary search is an efficient algorithm used to find the position of a target value within a sorted array. Unlike linear search, which checks each element one by one, binary search significantly reduces the number of comparisons needed by dividing the search interval in half with each step.

---

## **How it works**

##### **Initial Setup**:

- Identify the start (left) and end (right) indices of the array.

- Calculate the middle index: middle = Math.floor((left + right) / 2).

#### **Comparison**: Compare the target value with the middle element

 - If the middle element equals the target, the search is complete.

 - If the target is less than the middle element, narrow the search to the left half.

 - If the target is greater than the middle element, narrow the search to the right half.

#### **Termination**:

 - If the target is found, return the index of the target value.

- If the search space is exhausted (i.e., left > right), the target is not in the array, and the function returns -1.


![[binary-search-in-c-1.webp]]

---
## **Implementation**

```
function binarySearch(arr, targetVal) {

  let left = 0;

  let right = arr.length - 1;

  while (left <= right) {

    const middle = Math.floor((left + right) / 2);

    if (arr[middle] === targetVal) {

      return middle;

    } else if (arr[middle] < targetVal) {

      left = middle + 1;

    } else {

      right = middle - 1;

    }

  }

  return -1; // Target value not found

}

let arr = [2, 3, 4, 10, 40];

let targetVal = 10;

let result = binarySearch(arr, targetVal);

if (result !== -1) {

  console.log("Value", targetVal, "found at index", result);

} else {

  console.log("Value", targetVal, "not found");

}
```

