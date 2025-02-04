

> [!info] Info
> The Merge Sort algorithm is a divide-and-conquer algorithm that sorts an array by first breaking it down into smaller arrays, and then building the array back together the correct way so that it is sorted.

---

## **How it's work**



![[img_mergesort_long.png]]


---


## **Implementation**

```
function mergeSort(arr) {

  if (arr.length <= 1) {

    return arr;

  }

  const mid = Math.floor(arr.length / 2);

  const left = mergeSort(arr.slice(0, mid));

  const right = mergeSort(arr.slice(mid));

  const returnArray = []

  while (left.length !== 0 && right.length !== 0) {

    if (left[0] < right[0]) {

      returnArray.push(left.shift())

    } else {

      returnArray.push(right.shift())

    }

  }

  if (left.length > 0) {

    returnArray.push(...left)

  } else {

    returnArray.push(...right)

  }

  console.log(returnArray)

  console.log("\n")

  return returnArray

}

const unsortedArr = [12, 8, 9, 3, 11, 5, 4];

console.log("Sorted array:", mergeSort(unsortedArr));
```

---

## **:LiChevronRightCircle: Go to [[liner Search]]**

