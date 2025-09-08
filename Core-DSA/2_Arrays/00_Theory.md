Got it ✅ Let’s create a **clean and detailed theory guide about Arrays in Java** for your `DSA/Basics/Arrays/Theory.md`.

---

# 📘 Arrays in Java – Theory (For Core Java Learners & Developers)

## 🔹 1. Introduction

An **array** in Java is a **collection of similar data types** stored in **contiguous memory locations**.

* Arrays are **fixed in size** (cannot be resized after creation).
* Elements are indexed (starting from `0`).
* Arrays can be **1D, 2D, or multi-dimensional**.

Think of an array as **boxes kept in a straight line**, where each box holds one value.

---

## 🔹 2. Declaration and Initialization

### Declaration

```java
int[] arr;        // Preferred way
int arr[];        // Valid but less preferred
```

### Initialization

```java
int[] arr = new int[5];  // Array of size 5, default values = 0
String[] names = new String[3]; // Array of Strings, default values = null
```

### Combined Declaration + Initialization

```java
int[] nums = {10, 20, 30, 40};  // Size is auto-detected (4)
```

---

## 🔹 3. Default Values

When you create an array using `new`, Java fills it with default values:

| Data Type              | Default Value               |
| ---------------------- | --------------------------- |
| int, byte, short, long | `0`                         |
| float, double          | `0.0`                       |
| char                   | `'\u0000'` (null character) |
| boolean                | `false`                     |
| Objects (String, etc.) | `null`                      |

---

## 🔹 4. Accessing Elements

Elements are accessed by their **index**:

```java
int[] nums = {10, 20, 30};
System.out.println(nums[0]); // 10
System.out.println(nums[2]); // 30
```

⚠️ If you access an invalid index → **`ArrayIndexOutOfBoundsException`**.

---

## 🔹 5. Array Traversal

### Using a For Loop

```java
for (int i = 0; i < nums.length; i++) {
    System.out.println(nums[i]);
}
```

### Using Enhanced For Loop (For-each)

```java
for (int num : nums) {
    System.out.println(num);
}
```

---

## 🔹 6. Multi-dimensional Arrays

Java implements multi-dimensional arrays as **arrays of arrays**.

### 2D Array Example

```java
int[][] matrix = new int[3][3]; // 3x3 matrix

matrix[0][0] = 1;
matrix[0][1] = 2;

System.out.println(matrix[0][1]); // 2
```

### Initialization with Values

```java
int[][] mat = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};
```

---

## 🔹 7. Common Operations

1. **Finding Length**

```java
System.out.println(nums.length); // gives number of elements
```

2. **Copying Arrays**

```java
int[] copy = Arrays.copyOf(nums, nums.length);
```

3. **Sorting**

```java
Arrays.sort(nums); // In-place ascending sort
```

4. **Searching**

```java
int idx = Arrays.binarySearch(nums, 30);
```

---

## 🔹 8. Limitations of Arrays

* Fixed size (cannot grow/shrink).
* Cannot store mixed data types (must be homogeneous).
* No built-in methods for insertion/deletion (need `ArrayList` for dynamic behavior).

---

## 🔹 9. Arrays vs ArrayList

| Feature     | Array                       | ArrayList                                           |
| ----------- | --------------------------- | --------------------------------------------------- |
| Size        | Fixed                       | Dynamic                                             |
| Data Types  | Primitives & Objects        | Only Objects (uses wrappers for primitives)         |
| Performance | Faster (less overhead)      | Slightly slower                                     |
| Methods     | No inbuilt methods (manual) | Rich built-in methods (add, remove, contains, etc.) |

---

## 🔹 11. Time & Space Complexity

* **Access by index** → `O(1)`
* **Update by index** → `O(1)`
* **Search** → `O(n)` (linear), `O(log n)` (if sorted with binary search)
* **Insert/Delete** → `O(n)` (since shifting is needed)

---

✅ This theory gives a **solid foundation** for arrays in Java. Next step is to build **problem-solving templates** (like Reverse, Rotate, Max-Min, Kadane’s Algorithm, etc.) inside `Code/`.

---

| Problem                   | Concept             | File                      |
| ------------------------- | ------------------- | ------------------------- |
| Reverse Array             | In-place swapping   | `ReverseArray.java`       |
| Rotate Array              | Cyclic replacements | `RotateArray.java`        |
| Two Sum                   | HashMap basics      | `TwoSum.java`             |
| Find Max/Min              | Iteration           | `MaxMinElement.java`      |
| Second Largest            | Comparison          | `SecondLargest.java`      |
| Check Sorted Array        | Traversal           | `CheckSortedArray.java`   |
| Remove Duplicates         | Two Pointers        | `RemoveDuplicates.java`   |
| Move Zeroes               | Two Pointers        | `MoveZeroes.java`         |
| Missing Number            | XOR / Math          | `MissingNumber.java`      |
| Maximum Subarray (Kadane) | DP / Greedy         | `KadaneMaxSubarray.java`  |
| Prefix Sum                | Range sum queries   | `PrefixSum.java`          |
| Subarray Sum Equals K     | Prefix + HashMap    | `SubarraySumEqualsK.java` |
| Merge Sorted Arrays       | Two Pointers        | `MergeSortedArrays.java`  |
| Spiral Matrix             | Simulation          | `SpiralMatrix.java`       |


Would you like me to now create a **starter problem set list for Arrays** (from easy to hard, mapped to LeetCode/other platforms) so you can systematically fill your `Code/` folder?
