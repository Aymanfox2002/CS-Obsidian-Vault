

> [!info] Info
> Insertion Sort works by dividing the array into two parts: a **sorted part** and an **unsorted part**. It takes one element at a time from the unsorted part and inserts it into its correct position in the sorted part.

---
## **How It Works**

1. **Start with the first element:** Treat it as the initial sorted portion of the array.

2. **Pick each subsequent element:** Compare it with elements in the sorted part.

3. **Insert it in the correct place:** Shift elements as needed to make room.

4. **Repeat:** Continue this process for each element in the unsorted part until the entire array is sorted.

---

## **Implementation**

```
for (let i = 1; i < n; i++) {

  let insertIndex = i;

  let currentValue = myArray[i];

  for (let j = i - 1; j >= 0; j--) {

      if (myArray[j] > currentValue) {

          myArray[j + 1] = myArray[j];

          insertIndex = j;

      } else {

          break;

      }

  }

  myArray[insertIndex] = currentValue;

}
```

---

## **:LiArrowRightCircle: Go to [[Quick Sort]]**
