

> [!NOTE] Title
Quick Sort is a fast and efficient sorting algorithm that uses a divide-and-conquer approach to sort an array.


---
## **How it works**


  1. Choose a Pivot: Select an element from the array as the pivot. This can be any element, but common choices are the first, last, or middle element.

  2. Partitioning: Rearrange the array so that elements less than the pivot are on the left side, and elements greater than the pivot are on the right side.

  3. Recursion: Recursively apply the same process to the sub-arrays on the left and right of the pivot until the entire array is sorted.

---

## **Implementation**

```
const quickSort = (arr) => {

  if (arr.length <= 1) {

    return arr;

  }

  let pivot = arr[0];

  let leftArr = [];

  let rightArr = [];

  for (let i = 1; i < arr.length; i++) { // n

    if (arr[i] < pivot) {

      leftArr.push(arr[i]);

    } else {

      rightArr.push(arr[i]);

    }

  }

  return [...quickSort(leftArr), pivot, ...quickSort(rightArr)];

};

let arr = [3, 5, 4, 2, 1]

console.log(quickSort(arr))
```

---

## **:LiArrowRightCircle: Go To [[Counting Sort]]**
