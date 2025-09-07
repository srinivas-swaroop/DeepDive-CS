Perfect! Let’s **deep dive into the List interface**, focusing on **ArrayList and LinkedList** — covering **concepts, internal workings, syntax, methods, use-cases, performance, and examples** — aimed at **core Java learners and developers**.

Save as:

```
Java-Core/21_List_ArrayList_LinkedList.md
```

---

# 📄 Java List Interface – ArrayList & LinkedList

---

## 1. Introduction to List Interface

* **`List`** is an **ordered collection** in Java that **allows duplicates**.
* Elements can be **accessed by index** (`0` to `size()-1`).
* Part of **Java Collections Framework (JCF)**.

**Key points about List:**

1. Maintains **insertion order**.
2. Allows **duplicate elements**.
3. Provides **index-based access** to elements.
4. Common implementations: **ArrayList, LinkedList, Vector, Stack**.

---

## 2. Why Use List?

* When you need **ordering of elements**.
* When **duplicates are allowed**.
* When **index-based access** is required.
* Examples: storing students in a class, list of tasks, browsing history.

---

## 3. List Interface – Core Methods

| Method                  | Description                          |
| ----------------------- | ------------------------------------ |
| `add(E e)`              | Adds element to the end              |
| `add(int index, E e)`   | Inserts element at specific position |
| `get(int index)`        | Returns element at index             |
| `set(int index, E e)`   | Replaces element at index            |
| `remove(int index)`     | Removes element at index             |
| `remove(Object o)`      | Removes first occurrence of element  |
| `contains(Object o)`    | Checks if element exists             |
| `size()`                | Returns number of elements           |
| `indexOf(Object o)`     | Returns first index of element       |
| `lastIndexOf(Object o)` | Returns last index of element        |
| `clear()`               | Removes all elements                 |
| `isEmpty()`             | Checks if list is empty              |

---

## 4. ArrayList

### 4.1 Overview

* **ArrayList** = resizable array.
* Implements **List**, **RandomAccess**, **Cloneable**, **Serializable**.
* Stores elements **contiguously** in memory.
* Allows **fast random access** (`O(1)`) but **slow insert/delete in middle** (`O(n)`).

### 4.2 Syntax

```java
import java.util.ArrayList;
import java.util.List;

public class ArrayListDemo {
    public static void main(String[] args) {
        List<String> fruits = new ArrayList<>(); // Generic type

        // Add elements
        fruits.add("Apple");
        fruits.add("Banana");
        fruits.add("Cherry");
        fruits.add("Banana"); // Duplicate allowed

        // Access elements
        System.out.println(fruits.get(1)); // Banana

        // Modify element
        fruits.set(2, "Mango");

        // Remove element
        fruits.remove("Banana"); // removes first occurrence

        // Iterate
        for (String fruit : fruits) {
            System.out.println(fruit);
        }

        // Size
        System.out.println("Total fruits: " + fruits.size());
    }
}
```

### 4.3 Why This Syntax?

1. `List<String> fruits = new ArrayList<>();`

   * **Polymorphism**: reference type is List, object type is ArrayList.
   * Allows switching implementation easily.

2. `fruits.add(...)`

   * Adds element to dynamic array (resizes automatically if needed).

3. `fruits.get(index)`

   * Access element by index efficiently (`O(1)`).

---

### 4.4 Performance Summary (ArrayList)

| Operation       | Time Complexity |
| --------------- | --------------- |
| Access by index | O(1)            |
| Add at end      | Amortized O(1)  |
| Add at index    | O(n)            |
| Remove          | O(n)            |
| Search          | O(n)            |

✅ Best for **frequent access and iteration**, less frequent insert/remove in middle.

---

## 5. LinkedList

### 5.1 Overview

* **LinkedList** = doubly-linked list.
* Implements **List, Queue, Deque, Cloneable, Serializable**.
* Stores elements as **nodes** (data + pointers to next and previous).
* **Fast insert/delete** anywhere (`O(1)` if node reference is known), **slow random access** (`O(n)`).

### 5.2 Syntax

```java
import java.util.LinkedList;
import java.util.List;

public class LinkedListDemo {
    public static void main(String[] args) {
        List<String> tasks = new LinkedList<>();

        // Add elements
        tasks.add("Task1");
        tasks.add("Task2");
        tasks.add("Task3");

        // Add at index
        tasks.add(1, "Task1.5");

        // Access elements
        System.out.println(tasks.get(2)); // Task2

        // Remove element
        tasks.remove("Task1.5");

        // Iterate using lambda
        tasks.forEach(task -> System.out.println(task));
    }
}
```

### 5.3 Why This Syntax?

1. `List<String> tasks = new LinkedList<>();`

   * Polymorphism allows changing List implementation easily.

2. `tasks.add(1, "Task1.5")`

   * LinkedList adjusts pointers to insert in middle efficiently.

3. `tasks.forEach(...)`

   * Modern iteration using **lambda** expressions.

---

### 5.4 Performance Summary (LinkedList)

| Operation       | Time Complexity                  |
| --------------- | -------------------------------- |
| Access by index | O(n)                             |
| Add at end      | O(1)                             |
| Add at index    | O(n) to traverse, O(1) to insert |
| Remove          | O(n) to find, O(1) to remove     |
| Search          | O(n)                             |

✅ Best for **frequent insertions/deletions**, less frequent random access.

---

## 6. ArrayList vs LinkedList – Quick Comparison

| Feature          | ArrayList                          | LinkedList                |
| ---------------- | ---------------------------------- | ------------------------- |
| Internal Storage | Dynamic array                      | Doubly-linked nodes       |
| Access by index  | Fast (O(1))                        | Slow (O(n))               |
| Insert/Delete    | Slow in middle (O(n))              | Fast if node known (O(1)) |
| Memory           | Less (array)                       | More (pointers)           |
| Use Case         | Frequent access, few modifications | Frequent insert/delete    |

---

## 7. Common List Operations Example

```java
List<Integer> numbers = new ArrayList<>();
numbers.add(10);
numbers.add(20);
numbers.add(30);
numbers.add(10); // duplicate

// Check contains
System.out.println(numbers.contains(20)); // true

// Index of element
System.out.println(numbers.indexOf(10)); // 0
System.out.println(numbers.lastIndexOf(10)); // 3

// Remove by index
numbers.remove(2); // removes 30

// Clear list
numbers.clear();
```

---

## 8. Best Practices

* Use **ArrayList** for **random access**.
* Use **LinkedList** for **frequent insertions/deletions**.
* Always **use List interface** as reference type (`List<E> list = new ArrayList<>();`) for flexibility.
* Avoid using **legacy classes** like `Vector` unless thread-safe version is needed.
* Prefer **generics** for **type safety** (`List<String>`, `List<Integer>`).

---

## 9. Summary

* **List** = ordered, allows duplicates, indexed access.
* **ArrayList** = resizable array, fast random access, slower insertion/deletion in middle.
* **LinkedList** = doubly-linked list, fast insertion/deletion, slower random access.
* Use **polymorphism** to reference `List` interface.
* Knowing **internal structure** helps choose the right implementation for performance-critical applications.

---

If you want, the next step can be **Set interface deep dive**, including **HashSet, LinkedHashSet, TreeSet**, with **all methods, internal working, time complexity, and examples** for core learners and developers.

Do you want me to continue with **Set interface** next?
