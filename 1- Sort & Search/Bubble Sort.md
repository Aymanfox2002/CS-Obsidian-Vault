

> [!info]
> Bubble Sort is a simple algorithm that sorts an array by repeatedly stepping through the list, comparing adjacent elements, and swapping them if they are in the wrong order. The algorithm gets its name from the way larger elements "bubble up" to the end of the array.

---

## **How Bubble Sort Works:**

1. **Initial Pass**: Compare each pair of adjacent items in the array. If the first item is greater than the second, swap them.

2. **Repeat**: Continue comparing and swapping until the end of the array is reached. The largest unsorted item will be in its correct position at the end of the array.

3. **Reduce Range**: With each pass, the range of unsorted elements is reduced by one since the end of the array is sorted.

4. **Stop Early**: If a pass completes with no swaps, the array is already sorted, and the algorithm can stop early.

---

## **Implementation**

```
function bubbleSort(arr) {

  let n = arr.length;

  for (let i = 0; i < n - 1; i++) {

      let swapped = false;

      for (let j = 0; j < n - i - 1; j++) {

          if (arr[j] > arr[j + 1]) {

              [arr[j], arr[j + 1]] = [arr[j + 1], arr[j]];

              swapped = true;

          }

      }

      if (!swapped) {

          break;

      }

  }

  return arr;

}

let arr = [7, 3, 9, 12, 11];

console.log("Sorted array:", bubbleSort(arr));
```

---

## **:LiArrowBigRight: Go to [[Selection Sort]]**


