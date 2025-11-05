## 🧠 Arrays — Core Notes

### 1. Definition

An **array** is a **collection of elements** of the same data type, stored **in contiguous memory**.
It is the most basic linear data structure and serves as the foundation for others like stacks, queues, and hash tables.

---

## 🧮 Two-Dimensional Arrays

### 1. Concept

A **Two-Dimensional Array (2D Array)** is an **array of arrays**. Each element of the main array holds a **reference to another array**, forming a **matrix-like structure** (rows × columns). This structure is widely used in simulations, games, image processing, and mathematical computations.

In memory, it looks like this:

```
Row 0 → [a00, a01, a02, a03]
Row 1 → [a10, a11, a12, a13]
Row 2 → [a20, a21, a22, a23]
```

Here, `myArray[1][2]` accesses the element in the 2nd row, 3rd column.

### 2. Characteristics

* All sub-arrays (rows) contain the **same data type**.
* Memory layout is **row-major order** (elements of a row are stored sequentially).
* Each row is itself a **1D array reference**.

### 3. Declaration and Initialization (Java)

```java
int rows = 3;
int cols = 4;

int[][] my2DArray = new int[rows][cols];
```

This creates a 3×4 array (3 rows, 4 columns), capable of holding 12 integer values.

> `new` allocates the array on the heap and returns a reference to it.

You can also declare and initialize in one step:

```java
int[][] matrix = {
  {1, 2, 3, 4},
  {5, 6, 7, 8},
  {9, 10, 11, 12}
};
```

### 4. Common Errors — `NullPointerException`

If you only allocate memory for the rows and forget the columns, like:

```java
int[][] arr = new int[3][];  // Only rows allocated
arr[0][0] = 10;              // ❌ NullPointerException
```

You must allocate each sub-array:

```java
int[][] arr = new int[3][];
arr[0] = new int[4];
arr[1] = new int[4];
arr[2] = new int[4];
```

Now each row exists as a separate array.

### 5. Accessing Elements

```java
my2DArray[1][2] = 45;       // Assign value
int val = my2DArray[0][3];  // Retrieve value
```

> Indices start at 0: valid range = `[0 .. rows-1][0 .. cols-1]`

### 6. Example — Student Grades Table

Suppose there are 30 students and each takes 6 subjects. You can model this as:

```java
int[][] grades = new int[30][6];
```

Here:

* `grades[i][0..5]` → scores of student *i*
* You can calculate:

  * Average grade per student
  * Class average
  * Ranking, etc.

This structure allows easy iteration:

```java
for (int i = 0; i < 30; i++) {
    int total = 0;
    for (int j = 0; j < 6; j++) {
        total += grades[i][j];
    }
    double avg = total / 6.0;
    System.out.println("Student " + i + " avg: " + avg);
}
```

### 7. Memory Model

For an `int[3][4]` array:

```
Base + ((i * cols) + j) * sizeof(int)
```

This computes the memory address of `arr[i][j]`.

If each int = 4 bytes and base = 1000:

* `arr[0][0]` → 1000
* `arr[0][1]` → 1004
* `arr[1][0]` → 1016

---

## 🧊 Three-Dimensional Arrays

### 1. Concept

A **Three-Dimensional Array (3D Array)** extends the 2D array into another dimension — think of it as a **cube of data**.
Each element is indexed using **three indices (i, j, k)**, representing **depth, rows, and columns**.

Used in: graphics, volumetric data, 3D matrices, and physics simulations.

### 2. Declaration and Initialization

```java
int[][][] cube = new int[3][4][5];
```

This represents 3 layers, each containing a 4×5 2D grid.

You can initialize explicitly:

```java
int[][][] cube = {
  {
    {1, 2, 3},
    {4, 5, 6}
  },
  {
    {7, 8, 9},
    {10, 11, 12}
  }
};
```

### 3. Access Example

```java
cube[0][1][2] = 50;  // layer 0, row 1, column 2
int x = cube[1][0][0];
```

### 4. Memory Layout

Address of element in a 3D array:

```
Address(A[i][j][k]) = Base + ((i * rows * cols) + (j * cols) + k) * size
```

### 5. Visualization

```
Layer 0 → 2D plane 0
Layer 1 → 2D plane 1
Layer 2 → 2D plane 2
```

Each layer behaves as an independent 2D array.

---

### 🧩 Summary Cheatline

> **2D Array** = array of arrays (matrix) → indexed `[row][col]`
> **3D Array** = array of 2D arrays (cube) → indexed `[depth][row][col]`
