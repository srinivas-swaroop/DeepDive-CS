Perfect! Let’s do a **deep dive into the Map interface** in Java, covering **HashMap, LinkedHashMap, and TreeMap** — including **concepts, internal workings, syntax, methods, performance, and best practices** for **core Java learners and developers**.

Save as:

```
Java-Core/23_Map_HashMap_LinkedHashMap_TreeMap.md
```

---

# 🗺 Java Map Interface – HashMap, LinkedHashMap, TreeMap

---

## 1. Introduction to Map Interface

* **Map** = collection of **key-value pairs**.
* **Keys are unique**, values can be duplicate.
* **Does not extend Collection** interface but part of **Java Collections Framework**.

**Key points about Map:**

1. Each key maps to **exactly one value**.
2. Provides **fast lookup by key**.
3. Common implementations: **HashMap, LinkedHashMap, TreeMap**.

---

## 2. Why Use Map?

* When you need **associative data storage**.
* Examples: storing **username → userID**, **productID → productInfo**, **country → capital**.
* Allows **efficient retrieval, insertion, deletion** by key.

---

## 3. Map Interface – Core Methods

| Method                        | Description                          |
| ----------------------------- | ------------------------------------ |
| `put(K key, V value)`         | Adds or updates a key-value pair     |
| `get(Object key)`             | Returns value for key                |
| `remove(Object key)`          | Removes mapping for key              |
| `containsKey(Object key)`     | Checks if key exists                 |
| `containsValue(Object value)` | Checks if value exists               |
| `keySet()`                    | Returns Set of keys                  |
| `values()`                    | Returns Collection of values         |
| `entrySet()`                  | Returns Set of key-value entries     |
| `size()`                      | Returns number of mappings           |
| `isEmpty()`                   | Checks if map is empty               |
| `clear()`                     | Removes all mappings                 |
| `putAll(Map m)`               | Copies all mappings from another map |

---

## 4. HashMap

### 4.1 Overview

* **HashMap** = stores key-value pairs using **hash table**.
* Implements **Map, Serializable, Cloneable**.
* **Unordered** (no guarantee on iteration order).
* Allows **one null key and multiple null values**.
* **Not synchronized** by default.

**Internal Working:**

* Uses **array of buckets**; each bucket is a linked list or balanced tree (Java 8+) when collisions occur.
* Key's **hashCode** determines bucket index.

### 4.2 Syntax

```java
import java.util.HashMap;
import java.util.Map;

public class HashMapDemo {
    public static void main(String[] args) {
        Map<Integer, String> map = new HashMap<>();

        // Add entries
        map.put(1, "Alice");
        map.put(2, "Bob");
        map.put(3, "Charlie");
        map.put(2, "David"); // updates value for key 2

        // Access value
        System.out.println(map.get(2)); // David

        // Remove key
        map.remove(3);

        // Check contains
        System.out.println(map.containsKey(1)); // true
        System.out.println(map.containsValue("Alice")); // true

        // Iterate using entrySet
        for (Map.Entry<Integer, String> entry : map.entrySet()) {
            System.out.println(entry.getKey() + " -> " + entry.getValue());
        }
    }
}
```

**Why this syntax?**

* `Map<Integer, String> map = new HashMap<>();` → uses **Map interface** for flexibility.
* `map.put(key, value)` → adds or updates key-value pair.
* `entrySet()` → iterates over keys and values efficiently.

### 4.3 Performance (HashMap)

| Operation   | Average Time Complexity |
| ----------- | ----------------------- |
| put         | O(1)                    |
| get         | O(1)                    |
| remove      | O(1)                    |
| containsKey | O(1)                    |
| Iterate     | O(n)                    |

✅ Best for **fast key-based access**.

---

## 5. LinkedHashMap

### 5.1 Overview

* **LinkedHashMap** = **HashMap + LinkedList**.
* Maintains **insertion order** of keys.
* Slightly slower than HashMap due to maintaining order.

### 5.2 Syntax

```java
import java.util.LinkedHashMap;
import java.util.Map;

public class LinkedHashMapDemo {
    public static void main(String[] args) {
        Map<Integer, String> map = new LinkedHashMap<>();

        map.put(1, "Alice");
        map.put(2, "Bob");
        map.put(3, "Charlie");

        // Iteration preserves insertion order
        map.forEach((key, value) -> System.out.println(key + " -> " + value));
    }
}
```

**Why this syntax?**

* Preserves **order of insertion**.
* Ideal for **cache implementations** where order matters.

---

## 6. TreeMap

### 6.1 Overview

* **TreeMap** = implements **NavigableMap** using **Red-Black tree**.
* Maintains **keys in sorted order** (natural or custom comparator).
* **Null keys not allowed**; values can be null.
* Useful when **sorted key order** is required.

### 6.2 Syntax

```java
import java.util.Map;
import java.util.TreeMap;

public class TreeMapDemo {
    public static void main(String[] args) {
        Map<Integer, String> map = new TreeMap<>();

        map.put(50, "Alice");
        map.put(10, "Bob");
        map.put(30, "Charlie");

        // Keys are sorted
        map.forEach((key, value) -> System.out.println(key + " -> " + value));
        // Output: 10 -> Bob, 30 -> Charlie, 50 -> Alice

        // Remove key
        map.remove(30);
    }
}
```

**Why this syntax?**

* TreeMap automatically **sorts keys**.
* Can provide **custom Comparator** for custom sorting.

### 6.3 Performance (TreeMap)

| Operation   | Time Complexity |
| ----------- | --------------- |
| put         | O(log n)        |
| get         | O(log n)        |
| remove      | O(log n)        |
| containsKey | O(log n)        |
| Iterate     | O(n)            |

✅ Best for **sorted unique keys**.

---

## 7. Comparison – HashMap vs LinkedHashMap vs TreeMap

| Feature               | HashMap             | LinkedHashMap            | TreeMap              |
| --------------------- | ------------------- | ------------------------ | -------------------- |
| Order                 | No                  | Insertion order          | Sorted order         |
| Duplicates            | No keys, yes values | No keys, yes values      | No keys, yes values  |
| Null Key              | 1 allowed           | 1 allowed                | Not allowed          |
| Null Values           | Yes                 | Yes                      | Yes                  |
| Performance (get/put) | O(1)                | O(1)                     | O(log n)             |
| Use Case              | Fast access         | Maintain insertion order | Maintain sorted keys |

---

## 8. Best Practices

1. Use **HashMap** for **fast key-value access** when order is irrelevant.
2. Use **LinkedHashMap** for **predictable iteration order** (like LRU cache).
3. Use **TreeMap** for **sorted keys**.
4. Always use **Map interface** as reference type:

   ```java
   Map<Integer, String> map = new HashMap<>();
   ```
5. Avoid **null keys in TreeMap**; use comparator if needed.
6. Prefer `forEach` or `entrySet` for **efficient iteration**.

---

## 9. Summary

* **Map interface** = key-value pairs with **unique keys**.
* **HashMap** → fastest, unordered, allows null key.
* **LinkedHashMap** → maintains insertion order.
* **TreeMap** → maintains sorted key order.
* Use the right **Map implementation** based on **order, performance, and sorting requirements**.

---

Next, we can **deep dive into Queue and Deque interface**, including **PriorityQueue and ArrayDeque**, with **methods, performance, and examples**, which is crucial for **Java developers and learners**.

Do you want me to continue with **Queue and Deque** next?
