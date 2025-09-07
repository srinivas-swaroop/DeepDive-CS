Absolutely! Let’s do a **deep dive into the Set interface** in Java, including **HashSet, TreeSet, and LinkedHashSet** — covering **concepts, internal workings, syntax, methods, performance, and best practices** for **core Java learners and developers**.

Save as:

```
Java-Core/22_Set_HashSet_TreeSet_LinkedHashSet.md
```

---

# 🛡 Java Set Interface – HashSet, TreeSet, LinkedHashSet

---

## 1. Introduction to Set Interface

* **Set** is a **collection that contains no duplicate elements**.
* It **models the mathematical set abstraction**.
* Part of the **Java Collections Framework (JCF)**.

**Key points about Set:**

1. **No duplicates** → only one copy of each element is allowed.
2. **Unordered or ordered** depending on implementation.
3. Common implementations: **HashSet, LinkedHashSet, TreeSet**.

---

## 2. Why Use Set?

* When **uniqueness of elements** is required.
* Examples: storing **user IDs, email addresses, unique products**.
* Automatically prevents **duplicate data**.

---

## 3. Set Interface – Core Methods

| Method                    | Description                                |
| ------------------------- | ------------------------------------------ |
| `add(E e)`                | Adds element if not already present        |
| `remove(Object o)`        | Removes the specified element              |
| `contains(Object o)`      | Checks if element exists                   |
| `size()`                  | Returns number of elements                 |
| `isEmpty()`               | Checks if set is empty                     |
| `clear()`                 | Removes all elements                       |
| `iterator()`              | Returns iterator to traverse elements      |
| `addAll(Collection c)`    | Adds all elements from another collection  |
| `removeAll(Collection c)` | Removes all elements in another collection |

---

## 4. HashSet

### 4.1 Overview

* **HashSet** = stores elements using a **hash table**.
* Implements **Set, Serializable, Cloneable, Iterable**.
* **Does not maintain order**.
* Allows **null element** (one null).

**Key features:**

* Fast lookup: **O(1)** average for add, remove, contains.
* No duplicates automatically.
* Backed by **HashMap internally**.

### 4.2 Syntax

```java
import java.util.HashSet;
import java.util.Set;

public class HashSetDemo {
    public static void main(String[] args) {
        Set<String> fruits = new HashSet<>();

        // Add elements
        fruits.add("Apple");
        fruits.add("Banana");
        fruits.add("Mango");
        fruits.add("Apple"); // duplicate ignored

        // Iterate using enhanced for loop
        for (String fruit : fruits) {
            System.out.println(fruit);
        }

        // Check contains
        System.out.println("Contains Mango? " + fruits.contains("Mango"));

        // Remove element
        fruits.remove("Banana");

        // Size
        System.out.println("Total fruits: " + fruits.size());
    }
}
```

**Why this syntax?**

* `Set<String> fruits = new HashSet<>();`

  * Using **Set interface** ensures **flexibility** to switch implementation later.
* `fruits.add(...)` → adds element if **not already present**.
* **Iteration order is not guaranteed** because HashSet uses hashing.

---

### 4.3 Performance (HashSet)

| Operation | Average Time Complexity |
| --------- | ----------------------- |
| Add       | O(1)                    |
| Remove    | O(1)                    |
| Contains  | O(1)                    |
| Iterate   | O(n)                    |

✅ Best for **fast access and uniqueness**, order not important.

---

## 5. LinkedHashSet

### 5.1 Overview

* **LinkedHashSet** = **HashSet + LinkedList**.
* Maintains **insertion order** while keeping elements unique.
* Slightly slower than HashSet due to maintaining order.

### 5.2 Syntax

```java
import java.util.LinkedHashSet;
import java.util.Set;

public class LinkedHashSetDemo {
    public static void main(String[] args) {
        Set<String> fruits = new LinkedHashSet<>();

        fruits.add("Apple");
        fruits.add("Banana");
        fruits.add("Mango");
        fruits.add("Apple"); // duplicate ignored

        fruits.forEach(System.out::println); // maintains insertion order
    }
}
```

**Why this syntax?**

* `LinkedHashSet` preserves **insertion order**.
* `forEach(System.out::println)` → modern lambda-based iteration.

### 5.3 Performance (LinkedHashSet)

| Operation | Time Complexity |
| --------- | --------------- |
| Add       | O(1)            |
| Remove    | O(1)            |
| Contains  | O(1)            |
| Iterate   | O(n)            |

✅ Best for **unique elements + predictable iteration order**.

---

## 6. TreeSet

### 6.1 Overview

* **TreeSet** = implements **NavigableSet** using a **Red-Black tree** (self-balancing BST).
* Maintains **sorted order** of elements (natural ordering or custom comparator).
* **No duplicates**.
* **Null not allowed** (throws `NullPointerException` if comparator is used).

### 6.2 Syntax

```java
import java.util.Set;
import java.util.TreeSet;

public class TreeSetDemo {
    public static void main(String[] args) {
        Set<Integer> numbers = new TreeSet<>();

        numbers.add(50);
        numbers.add(10);
        numbers.add(30);
        numbers.add(20);
        numbers.add(30); // duplicate ignored

        numbers.forEach(System.out::println); // Sorted order: 10, 20, 30, 50

        // Check contains
        System.out.println("Contains 20? " + numbers.contains(20));

        // Remove element
        numbers.remove(10);
    }
}
```

**Why this syntax?**

* `TreeSet` automatically **sorts elements**.
* Suitable for **ordered, unique collections**.
* Can provide **custom sorting** using `Comparator`.

### 6.3 Performance (TreeSet)

| Operation | Time Complexity |
| --------- | --------------- |
| Add       | O(log n)        |
| Remove    | O(log n)        |
| Contains  | O(log n)        |
| Iterate   | O(n)            |

✅ Best for **sorted unique elements**, e.g., leaderboards, priority elements.

---

## 7. Summary – HashSet vs LinkedHashSet vs TreeSet

| Feature            | HashSet            | LinkedHashSet            | TreeSet         |
| ------------------ | ------------------ | ------------------------ | --------------- |
| Order              | No                 | Insertion order          | Sorted order    |
| Duplicates         | No                 | No                       | No              |
| Null Allowed       | Yes (1 null)       | Yes (1 null)             | No              |
| Lookup Performance | O(1)               | O(1)                     | O(log n)        |
| Use Case           | Fast unique access | Unique + insertion order | Unique + sorted |

---

## 8. Best Practices

1. Use **HashSet** for **fast, unordered, unique elements**.
2. Use **LinkedHashSet** when **order matters**.
3. Use **TreeSet** when **sorted order is required**.
4. Always use **Set interface** for reference type:

   ```java
   Set<String> set = new HashSet<>();
   ```
5. Avoid **null in TreeSet**, prefer **Comparator for custom sorting**.

---

## 9. Summary

* **Set interface** = collection of **unique elements**.
* **HashSet** → fast, unordered, allows null.
* **LinkedHashSet** → maintains insertion order.
* **TreeSet** → maintains sorted order, does not allow null.
* Choosing the right **Set implementation** depends on **order, performance, and sorting requirements**.

---

Next, we can **deep dive into Map interface**, including **HashMap, LinkedHashMap, TreeMap**, with **all methods, internal structure, performance, and examples** — crucial for **Java developers and core learners**.

Do you want me to continue with **Map interface** next?
