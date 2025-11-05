## 🧠 Arrays & Lists — Core Notes

### 1. What Is a List?

A **List** in Java is a **dynamic collection** that can store ordered elements and allows duplicates. Unlike arrays, lists can **resize automatically** and provide flexible methods for insertion, deletion, and traversal.

---

## 📘 Introduction to Lists

Lists are part of the `java.util` package and are among the most commonly used data structures in Java. They extend the **Collection interface** and introduce index-based element access.

### Key Features

* **Ordered collection:** Elements maintain their insertion order.
* **Allow duplicates:** Unlike sets, lists can contain repeated elements.
* **Indexed access:** Retrieve, update, or remove elements via index.
* **Dynamic sizing:** Lists automatically grow or shrink.

### Syntax

```java
import java.util.*;

List<Integer> numbers = new ArrayList<>();
```

Here, `List` is the interface and `ArrayList` is one of its implementations.

---

## 🧩 ArrayList — Common Implementation

An **ArrayList** is a **resizable array** that provides fast random access and dynamic resizing.

### Properties

* Internally backed by a **dynamic array**.
* Allows **random access** in `O(1)` time.
* **Insertion** and **deletion** (except at the end) are `O(n)` due to shifting elements.

### Example: Creating and Using a List

```java
import java.util.*;

public class Example {
    public static void main(String[] args) {
        List<String> fruits = new ArrayList<>();

        // Add elements
        fruits.add("Apple");
        fruits.add("Banana");
        fruits.add("Cherry");

        // Access elements
        System.out.println(fruits.get(1)); // Output: Banana

        // Remove element
        fruits.remove("Apple");

        // Size of list
        System.out.println(fruits.size()); // Output: 2

        // Iterate
        for (String fruit : fruits) {
            System.out.println(fruit);
        }
    }
}
```

### Time Complexity

| Operation       | Average Case |
| --------------- | ------------ |
| Access by index | `O(1)`       |
| Insert (end)    | `O(1)`       |
| Insert (middle) | `O(n)`       |
| Delete by index | `O(n)`       |
| Search by value | `O(n)`       |

---

## 🔢 1D Lists

A **1D List** behaves similarly to a 1D array but can dynamically expand or shrink.

### Declaration and Initialization

```java
List<Integer> numbers = new ArrayList<>();
numbers.add(10);
numbers.add(20);
numbers.add(30);
```

### Iterating a 1D List

```java
for (int num : numbers) {
    System.out.println(num);
}
```

### Modifying Elements

```java
numbers.set(1, 25);  // Change 20 → 25
```

### Removing Elements

```java
numbers.remove(0);  // Remove first element
```

---

## 🧮 2D Lists

A **2D List** in Java is a **list of lists**, allowing storage of elements in a grid-like structure (rows and columns).
Useful for representing matrices, tables, and game boards.

### Declaration & Initialization

```java
List<List<Integer>> matrix = new ArrayList<>();

for (int i = 0; i < 3; i++) {
    matrix.add(new ArrayList<>());
}

matrix.get(0).add(1);
matrix.get(0).add(2);
matrix.get(1).add(3);
matrix.get(2).add(4);
```

### Accessing Elements

```java
int value = matrix.get(1).get(0);  // Access row 1, column 0
```

### Iterating Through a 2D List

```java
for (List<Integer> row : matrix) {
    for (int val : row) {
        System.out.print(val + " ");
    }
    System.out.println();
}
```

### Modifying Elements

```java
matrix.get(0).set(1, 10);  // Modify element at row 0, column 1
```

### Finding Dimensions

```java
int rows = matrix.size();
int cols = matrix.get(0).size();
System.out.println("Rows: " + rows + ", Columns: " + cols);
```

### Example — 2D Grades Table

```java
List<List<Integer>> grades = new ArrayList<>();

for (int i = 0; i < 3; i++) {
    grades.add(new ArrayList<>(Arrays.asList(85, 90, 88)));
}

for (int i = 0; i < grades.size(); i++) {
    System.out.println("Student " + (i + 1) + " Grades: " + grades.get(i));
}
```

---

### 🧩 Summary Cheatline

> **List** = dynamic ordered collection (allows duplicates).
> **ArrayList** = resizable array-based List with fast random access.
> **2D List** = List of Lists → grid/matrix structure with dynamic resizing.
