## Sorting Algorithms

<details>
<summary><strong style="font-size: 1.4em"> Brute Force Sort (Selection Sort)</strong></summary>

- **How it works:** Imagine you have a row of numbered cards. You find the smallest card and move it to the front. Then you look for the next smallest from the remaining cards and move it next, and so on, until all cards are sorted.
- **Best, poor, and average outcomes:** O(n²), O(n²), O(n²)
- **JavaScript example and outcome:**

```javascript
  function selectionSort(arr) {
      let n = arr.length;
      for (let i = 0; i < n; i++) {
          let minIndex = i;
          for (let j = i + 1; j < n; j++) {
              if (arr[j] < arr[minIndex]) {
                  minIndex = j;
              }
          }
          [arr[i], arr[minIndex]] = [arr[minIndex], arr[i]];
      }
      return arr;
  }
  console.log(selectionSort([5, 3, 6, 2, 10]));
  ```
</details>

<details>
<summary><strong style="font-size: 1.4em"> Bubble Sort</strong></summary>

- **How it works:** Think of soda bubbles rising up. You repeatedly swap neighboring cards if they're in the wrong order, moving the largest unsorted card to its correct place, like a bubble rising to the top.
- **Best, poor, and average outcomes:** O(n), O(n²), O(n²)
- **JavaScript example and outcome:**

```javascript
  function bubbleSort(arr) {
      let n = arr.length;
      let swapped;
      do {
          swapped = false;
          for (let i = 1; i < n; i++) {
              if (arr[i - 1] > arr[i]) {
                  [arr[i - 1], arr[i]] = [arr[i], arr[i - 1]];
                  swapped = true;
              }
          }
          n--;
      } while (swapped);
      return arr;
  }
  console.log(bubbleSort([5, 3, 6, 2, 10]));
  ```
</details>

<details>
<summary><strong style="font-size: 1.4em"> Insertion Sort</strong></summary>

- **How it works:** Like sorting a hand of cards. You take one card at a time and insert it into its correct position in the already sorted part of the hand.
- **Best, poor, and average outcomes:** O(n), O(n²), O(n²)
- **JavaScript example and outcome:**

```javascript
  function insertionSort(arr) {
      let n = arr.length;
      for (let i = 1; i < n; i++) {
          let current = arr[i];
          let j = i - 1;
          while (j >= 0 && arr[j] > current) {
              arr[j + 1] = arr[j];
              j--;
          }
          arr[j + 1] = current;
      }
      return arr;
  }
  console.log(insertionSort([5, 3, 6, 2, 10]));
  ```
</details>

<details>
<summary><strong style="font-size: 1.4em"> Merge Sort</strong></summary>

- **How it works:** Imagine breaking a deck of cards into two piles, then each of those into smaller piles, until you have piles that can't be broken down further. Then merge them back together in order, from smallest to largest.
- **Best, poor, and average outcomes:** O(n log n), O(n log n), O(n log n)
- **JavaScript example and outcome:**

```javascript
  function mergeSort(arr) {
      if (arr.length < 2) {
          return arr;
      }
      const middle = Math.floor(arr.length / 2);
      const left = arr.slice(0, middle);
      const right = arr.slice(middle);
      return merge(mergeSort(left), mergeSort(right));
  }

  function merge(left, right) {
      let result = [];
      while (left.length && right.length) {
          if (left[0] <= right[0]) {
              result.push(left.shift());
          } else {
              result.push(right.shift());
          }
      }
      return result.concat(left.length ? left : right);
  }

  console.log(mergeSort([5, 3, 6, 2, 10]));
```
</details>

<details>
<summary><strong style="font-size: 1.4em"> Quick Sort</strong></summary>

- **How it works:** Pick a "pivot" card. Arrange all cards that are smaller to one side of the pivot, and those that are bigger to the other. Now, do the same for each side until all cards are sorted.
- **Best, poor, and average outcomes:** O(n log n), O(n²), O(n log n)
- **JavaScript example and outcome:**

```javascript
  function quickSort(arr) {
      if (arr.length <= 1) {
          return arr;
      }
      let pivot = arr[arr.length - 1];
      let left = [];
      let right = [];
      for (let i = 0; i < arr.length - 1; i++) {
          if (arr[i] < pivot) {
              left.push(arr[i]);
          } else {
              right.push(arr[i]);
          }
      }
      return [...quickSort(left), pivot, ...quickSort(right)];
  }
  console.log(quickSort([5, 3, 6, 2, 10]));
  ```
</details>

<details>
<summary><strong style="font-size: 1.4em"> Heap Sort</strong></summary>

- **How it works:** Imagine organizing your toys in a tree where every toy is bigger than the toys directly below it. Remove the biggest toy and rearrange the rest, then repeat until all toys are sorted.
- **Best, poor, and average outcomes:** O(n log n), O(n log n), O(n log n)
- **JavaScript example and outcome:**

```javascript
  function heapSort(arr) {
      let n = arr.length;
      // Build heap (rearrange array)
      for (let i = Math.floor(n / 2) - 1; i >= 0; i--)
          heapify(arr, n, i);
      // One by one extract an element from heap
      for (let i = n - 1; i > 0; i--) {
          // Move current root to end
          [arr[0], arr[i]] = [arr[i], arr[0]];
          // call max heapify on the reduced heap
          heapify(arr, i, 0);
      }
      return arr;
  }

  function heapify(arr, n, i) {
      let largest = i; // Initialize largest as root
      let l = 2 * i + 1; // left = 2*i + 1
      let r = 2 * i + 2; // right = 2*i + 2
      // If left child is larger than root
      if (l < n && arr[l] > arr[largest])
          largest = l;
      // If right child is larger than largest so far
      if (r < n && arr[r] > arr[largest])
          largest = r;
      // If largest is not root
      if (largest != i) {
          [arr[i], arr[largest]] = [arr[largest], arr[i]];
          // Recursively heapify the affected sub-tree
          heapify(arr, n, largest);
      }
  }
  console.log(heapSort([5, 3, 6, 2, 10]));
  ```
</details>

<details>
<summary><strong style="font-size: 1.4em"> Counting Sort</strong></summary>

- **How it works:** Imagine you have lots of apples, each marked with a number from 1 to 10. You count how many apples have each number, then put them back in order starting from the smallest number to the largest based on your count.
- **Best, poor, and average outcomes:** O(n + k), O(n + k), O(n + k) (where k is the range of the input)
- **JavaScript example and outcome:**

```javascript
  function countingSort(arr, max) {
      let count = new Array(max + 1).fill(0);
      arr.forEach(val => count[val]++);
      let k = 0;
      for (let i = 0; i < count.length; i++) {
          while (count[i] > 0) {
              arr[k++] = i;
              count[i]--;
          }
      }
      return arr;
  }
  console.log(countingSort([5, 3, 6, 2, 10], 10));
  ```
</details>

<details>
<summary><strong style="font-size: 1.4em"> Radix Sort</strong></summary>

- **How it works:** Think about sorting a deck of playing cards by first organizing them by number, ignoring the suit. Then, sort by suit within each number. Radix sort does something similar by sorting first by the least significant digit and moving to the most significant.
- **Best, poor, and average outcomes:** O(nk), O(nk), O(nk) (where n is the number of elements and k is the number of passes of the sorting algorithm)
- **JavaScript example and outcome:**

```javascript
  function radixSort(arr) {
      const maxNum = Math.max(...arr) * 10;
      let divisor = 10;
      while (divisor < maxNum) {
          let buckets = [...Array(10)].map(() => []);
          for (let num of arr) {
              buckets[Math.floor((num % divisor) / (divisor / 10))].push(num);
          }
          arr = [].concat(...buckets);
          divisor *= 10;
      }
      return arr;
  }
  console.log(radixSort([5, 3, 6, 2, 10]));
  ```
</details>

## Time Complexities

1. **O(n)**: Imagine walking along a line of toy blocks just once, touching each block as you pass. You do a task once for each item.
2. **O(n log n)**: Like sorting storybooks into piles, sort each pile, then put them all back together. You do a little bit of work (log n) for each book (n).
3. **O(n²)**: Picture a square made of toy blocks. Each time you add a row and a column, the square grows much faster. You're doing a task for every pair of blocks.
4. **O(n + k)**: You have n apples and k baskets. You handle each apple once (n) and do a little work for each basket (k).

