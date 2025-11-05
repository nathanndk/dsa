## 🧠 Arrays — Core Notes

### 1. Definition

An **array** is a **collection of elements** of the same data type, stored **in contiguous memory**.
It is the most basic linear data structure and serves as the foundation for others like stacks, queues, and hash tables.

### 2. Key Properties

* **Fixed Size**: Defined at creation; cannot be resized dynamically (in Java or C).
* **Homogeneous Elements**: All elements share the same data type.
* **Contiguous Memory**: Enables constant-time (`O(1)`) access via index.
* **Indexed Access**: The index starts at `0` and goes up to `size - 1`.

  * Access formula (low-level):
    `Address(A[i]) = Base_Address + (i * size_of_element)`

### 3. Why Use Arrays

Arrays allow:

* **Random Access** — retrieve or modify any element directly.
* **Cache Efficiency** — elements are stored sequentially in memory.
* **Foundational Use** — form the base for higher-level structures (matrix, heap, etc.).

### 4. Array Declaration & Initialization (Java)

```java
// Declaration only
int[] arr1;
int arr2[];

// Declaration + Initialization
arr1 = new int[5];

// Combined
int[] arr3 = new int[5];

// Literal initialization
int[] arr4 = {10, 20, 30, 40, 50};
```

> Uninitialized integer arrays are filled with zeros by default.

### 5. Accessing and Updating Elements

```java
arr3[2] = 99;        // update element at index 2
int x = arr3[0];     // access first element
```

Trying to access `arr3[5]` (out of range) → `ArrayIndexOutOfBoundsException`.

### 6. Arrays in Memory

In Java:

* Arrays are **objects** allocated on the heap.
* The variable holds a **reference** to the memory address of the first element.

Example:
`int[] a = new int[3];`
→ `a` holds a pointer to the first integer’s memory location.

In low-level view (C-style):

```text
Index:  0   1   2
Data:  [5] [9] [2]
Addr: 100 104 108  (assuming 4 bytes per int)
```

### 7. Common Operations & Time Complexity

| Operation                      | Time Complexity   |
| ------------------------------ | ----------------- |
| Access element                 | `O(1)`            |
| Update element                 | `O(1)`            |
| Insert at end (static array)   | `O(1)` (if space) |
| Insert at index (shift)        | `O(n)`            |
| Delete element                 | `O(n)`            |
| Traverse entire array          | `O(n)`            |
| Search (unsorted)              | `O(n)`            |
| Search (sorted, binary search) | `O(log n)`        |

### 8. Types of Arrays

* **1D Array** — simplest, linear sequence.
* **2D Array (Matrix)** — array of arrays, accessed as `a[i][j]`.

  ```java
  int[][] matrix = new int[3][4];  // 3 rows, 4 columns
  ```
* **Jagged Array** — a 2D array where each row has different length.

### 9. Memory Layout in Multi-D Arrays

For a matrix `a[m][n]`,
Memory layout (row-major):
`Address(a[i][j]) = Base + ((i * n) + j) * size_of_element`

### 10. Advantages

* Simple to implement.
* Direct access to elements.
* Strong cache locality → fast iteration.

### 11. Limitations

* Fixed size — can’t grow dynamically.
* Insertion and deletion are expensive (`O(n)`).
* Must store homogeneous data types.

### 12. Dynamic Alternatives

* **ArrayList (Java)** — grows automatically.
* **Vector (C++ STL)** — resizable array.
* **List (Python)** — dynamic array abstraction.

### 13. Example Problems

1. **Reverse an array in-place**

   ```java
   for (int i = 0; i < n / 2; i++) {
       int temp = arr[i];
       arr[i] = arr[n - i - 1];
       arr[n - i - 1] = temp;
   }
   ```
2. **Find the maximum element**

   ```java
   int max = arr[0];
   for (int i = 1; i < arr.length; i++) {
       if (arr[i] > max) max = arr[i];
   }
   ```
3. **Compute average**

   ```java
   double sum = 0;
   for (int v : arr) sum += v;
   double avg = sum / arr.length;
   ```

### 14. Relation to Other Data Structures

According to *Sedgewick* and *Karumanchi*:
Arrays underpin more complex ADTs:

* **Stack/Queue** — arrays with restricted operations.
* **Hash Table** — uses array as the base for buckets.
* **Matrix & Graphs** — adjacency representations rely on arrays.

---

### 🧩 Summary Cheatline

> **Array** = contiguous memory + indexed access + fixed size + homogeneous type.
