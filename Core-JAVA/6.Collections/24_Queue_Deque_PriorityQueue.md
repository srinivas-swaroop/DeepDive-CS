Absolutely! Let’s do a **comprehensive deep dive into Queue and Deque in Java**, including **PriorityQueue**, covering **concepts, internal workings, syntax, methods, performance, and best practices** for **core Java learners and developers**.

Save as:

```
Java-Core/24_Queue_Deque_PriorityQueue.md
```

---

# 🛎 Java Queue, Deque, and PriorityQueue

---

## 1. Introduction to Queue Interface

* **Queue** = a collection used to **hold elements prior to processing**.
* Follows **FIFO (First In, First Out)** principle.
* Part of **Java Collections Framework**.
* Implementations: **LinkedList, PriorityQueue, ArrayDeque**.

**Key points about Queue:**

1. **FIFO order** → first element added is first removed.
2. Supports operations like **enqueue (add)** and **dequeue (remove)**.
3. Can be used as **task scheduling, message queues, buffer systems**.

---

## 2. Queue Interface – Core Methods

| Method       | Description                                              |
| ------------ | -------------------------------------------------------- |
| `add(E e)`   | Inserts element, throws exception if fails               |
| `offer(E e)` | Inserts element, returns false if fails                  |
| `remove()`   | Removes and returns head, throws exception if empty      |
| `poll()`     | Removes and returns head, returns null if empty          |
| `element()`  | Returns head without removing, throws exception if empty |
| `peek()`     | Returns head without removing, returns null if empty     |

---

## 3. PriorityQueue

### 3.1 Overview

* **PriorityQueue** = Queue where **elements are ordered based on priority**.
* Implements **Queue, Serializable, Iterable, Collection**.
* Default **natural ordering** (ascending) or **custom Comparator**.
* **Null elements not allowed**.

### 3.2 Syntax

```java
import java.util.PriorityQueue;
import java.util.Queue;

public class PriorityQueueDemo {
    public static void main(String[] args) {
        Queue<Integer> pq = new PriorityQueue<>();

        // Add elements
        pq.add(50);
        pq.add(10);
        pq.add(30);

        // Head element (smallest)
        System.out.println("Head: " + pq.peek()); // 10

        // Remove elements in priority order
        while (!pq.isEmpty()) {
            System.out.println(pq.poll()); // 10, 30, 50
        }
    }
}
```

**Why this syntax?**

* `Queue<Integer> pq = new PriorityQueue<>();` → uses **Queue interface** for flexibility.
* `peek()` → retrieves head without removing.
* `poll()` → retrieves and removes head.

### 3.3 PriorityQueue with Comparator

```java
Queue<Integer> maxPQ = new PriorityQueue<>((a, b) -> b - a); // Max heap
maxPQ.add(10);
maxPQ.add(50);
maxPQ.add(30);

System.out.println(maxPQ.poll()); // 50
```

✅ Allows **custom ordering**.

---

### 3.4 Performance (PriorityQueue)

| Operation | Time Complexity |
| --------- | --------------- |
| add       | O(log n)        |
| poll      | O(log n)        |
| peek      | O(1)            |
| remove    | O(n)            |

✅ Best for **task scheduling, priority handling**.

---

## 4. Deque Interface

* **Deque** = Double-Ended Queue.
* Elements can be **added/removed at both ends**.
* Implements **Queue interface**.
* Implementations: **ArrayDeque, LinkedList**.
* Can be used as **stack (LIFO) or queue (FIFO)**.

---

### 4.1 Deque Methods

| Method            | Description                             |
| ----------------- | --------------------------------------- |
| `addFirst(E e)`   | Insert at front                         |
| `addLast(E e)`    | Insert at end                           |
| `offerFirst(E e)` | Insert at front, returns false if fails |
| `offerLast(E e)`  | Insert at end, returns false if fails   |
| `removeFirst()`   | Remove from front                       |
| `removeLast()`    | Remove from end                         |
| `pollFirst()`     | Remove front, return null if empty      |
| `pollLast()`      | Remove end, return null if empty        |
| `getFirst()`      | Get front element without removing      |
| `getLast()`       | Get last element without removing       |
| `peekFirst()`     | Retrieve front, return null if empty    |
| `peekLast()`      | Retrieve last, return null if empty     |

---

### 4.2 ArrayDeque Example

```java
import java.util.ArrayDeque;
import java.util.Deque;

public class ArrayDequeDemo {
    public static void main(String[] args) {
        Deque<String> deque = new ArrayDeque<>();

        // Add elements
        deque.addFirst("Task1");
        deque.addLast("Task2");
        deque.addLast("Task3");

        // Peek front and end
        System.out.println("First: " + deque.peekFirst()); // Task1
        System.out.println("Last: " + deque.peekLast()); // Task3

        // Remove elements
        deque.removeFirst();
        deque.removeLast();

        deque.forEach(System.out::println); // Task2
    }
}
```

**Why this syntax?**

* `Deque<String> deque = new ArrayDeque<>();` → use **Deque interface** for flexibility.
* Methods like `addFirst/addLast` provide **double-ended operations**.

---

### 4.3 Performance (ArrayDeque)

| Operation            | Time Complexity |
| -------------------- | --------------- |
| Add/Remove front/end | O(1)            |
| Access               | O(n)            |

✅ Best for **stack and queue implementations without capacity restrictions**.

---

## 5. LinkedList as Queue/Deque

* `LinkedList` also implements **Queue and Deque**.
* Suitable for **frequent insertions/deletions**.
* Slower **random access** (`O(n)`).

```java
Deque<Integer> deque = new LinkedList<>();
deque.addFirst(10);
deque.addLast(20);
deque.pollFirst(); // 10
deque.pollLast();  // 20
```

---

## 6. Queue vs PriorityQueue vs Deque – Quick Comparison

| Feature            | Queue (LinkedList) | PriorityQueue   | Deque (ArrayDeque) |
| ------------------ | ------------------ | --------------- | ------------------ |
| Order              | FIFO               | Priority order  | FIFO or LIFO       |
| Duplicate elements | Allowed            | Allowed         | Allowed            |
| Null elements      | Allowed            | Not allowed     | Allowed            |
| Access             | Head only          | Head (priority) | Front/End          |
| Use Case           | Task scheduling    | Priority tasks  | Stack/Queue combo  |

---

## 7. Use Cases

1. **Queue** → Print jobs, task scheduling.
2. **PriorityQueue** → Event-driven simulation, CPU scheduling.
3. **Deque / ArrayDeque** → Browser history, undo/redo, stack operations.

---

## 8. Best Practices

1. Always **use interfaces as reference types** (`Queue`, `Deque`).
2. **ArrayDeque** is preferable over **Stack** for LIFO operations.
3. **LinkedList** suitable when frequent insert/delete is needed.
4. **PriorityQueue** → use Comparator for custom ordering.
5. Avoid null in **PriorityQueue** or **TreeSet-based queues**.

---

## 9. Summary

* **Queue** → FIFO, basic operations: `offer/poll/peek`.
* **PriorityQueue** → ordered by priority, use comparator if needed.
* **Deque** → double-ended queue, supports **stack and queue operations**.
* **ArrayDeque** → fast, resizable, no capacity restrictions.
* **LinkedList** → flexible, suitable for frequent modifications.

---

Next, we can **cover Java Collections Utility classes** like **Collections and Arrays**, including **sorting, searching, reverse, shuffle, synchronized collection**, which are crucial **tools for Java developers**.

Do you want me to continue with **Collections utility class** next?
