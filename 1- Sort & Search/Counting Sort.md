

> [!info] Info
> **Counting Sort** is an algorithm that sorts an array by counting the occurrences of each distinct value. It is particularly efficient when the range of the possible values is smaller than the number of elements in the array. Unlike comparison-based algorithms, Counting Sort does not compare elements but rather relies on counting occurrences.


---

## **How Counting Sort Works**

**Create a Count Array:** A new array (countArray) is created to store the count of each distinct value in the input array.

**Count Occurrences:** Iterate through the input array, and for each value, increment the corresponding index in countArray to reflect how many times each value occurs.

**Build the Sorted Array:** Using the countArray, reconstruct the sorted array by appending the correct number of elements for each value in increasing order.

**Conditions for Counting Sort:**-
 1. **Integer Values:** Counting Sort only works with integers since it relies on indexing to count occurrences.

 2. **Non-Negative Values:** The algorithm usually assumes non-negative integers, as negative indices in an array are invalid.

 3. **Limited Range of Values:** The algorithm is efficient only when the range of values (k) is smaller than the number of elements (n) in the input array.

---

## **Implementation**

```
function countingSort(arr) {

  const maxVal = Math.max(...arr);

  const count = new Array(maxVal + 1).fill(0);

  while (arr.length > 0) {

      const num = arr.shift();

      count[num] += 1;

  }

  for (let i = 0; i < count.length; i++) {

      while (count[i] > 0) {

          arr.push(i);

          count[i] -= 1;

      }

  }

  return arr;

}

const unsortedArr = [4, 2, 2, 6, 3, 3, 1, 6, 5, 2, 3];

const sortedArr = countingSort(unsortedArr);

console.log("Sorted array:", sortedArr);
```

---

## **:LiArrowRightCircle: Go to [[Radix Sort]]**
