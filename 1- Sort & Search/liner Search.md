
> [!NOTE] Info
> **Linear search** is one of the simplest search algorithms. It checks each element in a list sequentially until it finds the target value or reaches the end of the list. Although it's not the most efficient algorithm for large datasets, it's easy to understand and implement.


---

## **How it's work**

Linear search works by starting from the first element of an array and comparing each element with the target value. If it finds the target value, it returns the index where the target is located. If the target value isn't found after checking all elements, the function returns -1 to indicate that the target is not in the array.

## **Steps**

 1. **Start at the first element** of the array.
 2. **Compare the current element** with the target value.
 3. **If they match,** return the index of the current element.
 4. **If they don't match,** move to the next element.
 5. **Repeat** the process until the end of the array.
 6. **If the target is not found,** return -1.

---

## **Implementation**

```
function linearSearch(arr, targetVal) {

  // Iterate through each element in the array

  for (let i = 0; i < arr.length; i++) {

      // If the current element matches the target, return its index

      if (arr[i] === targetVal) {

          return i;

      }

  }

  // If the target value is not found, return -1

  return -1;

}

// Example usage

let arr = [3, 7, 2, 9, 5];

let targetVal = 9;

let result = linearSearch(arr, targetVal);

if (result !== -1) {

  console.log("Value", targetVal, "found at index", result);

} else {

  console.log("Value", targetVal, "not found");
  }
```

---

## **:LiArrowRightCircle: Go to [[Binary Search]]**

