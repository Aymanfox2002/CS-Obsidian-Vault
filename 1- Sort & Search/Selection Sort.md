

> [!info] Info
> **Selection Sort** is an algorithm that sorts an array by repeatedly finding the lowest value and moving it to the front of the unsorted portion of the array.

---

## **It works as follows**

1. **Find the Minimum Value:** Iterate through the array to locate the lowest value.

2. **Move to Front:** Swap this lowest value with the first element of the unsorted part of the array.

3. **Repeat:** Continue this process, each time narrowing down the unsorted portion, until the entire array is          sorted.

---

## **Implementation**

```
let myArray = [64, 34, 25, 12, 22, 11, 90, 5];

let n = myArray.length;

for (let i = 0; i < n; i++) {

    let minIndex = i;

    for (let j = i + 1; j < n; j++) {

        if (myArray[j] < myArray[minIndex]) {

            minIndex = j;

        }

    }

    // Swap values

    [myArray[i], myArray[minIndex]] = [myArray[minIndex], myArray[i]];

}

console.log("Sorted array:", myArray);
```

---

## **:LiArrowRightCircle: Go to [[Insertion Sort]]**
 
 