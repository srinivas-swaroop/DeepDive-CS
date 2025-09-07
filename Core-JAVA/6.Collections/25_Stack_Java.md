Absolutely! Let’s do a **comprehensive deep dive into Stack in Java**, covering **concepts, internal workings, syntax, methods, performance, and best practices** for **core Java learners and developers**. I’ll also include the **modern recommended alternatives** since `Stack` is somewhat legacy.

Save as:

```
Java-Core/25_Stack_Java.md
```

---

# 🗂 Java Stack

---

## 1. Introduction to Stack

* **Stack** = a collection that follows **LIFO (Last In, First Out)** principle.
* Think of it as a **stack of plates**: last one added is the first one removed.
* Common **use cases**:

  1. Undo/redo functionality in editors
  2. Expression evaluation (infix, postfix, prefix)
  3. Backtracking algorithms (maze, recursion)
  4. Function call management (call stack)

---

## 2. Java Stack Class

* Part of **`java.util` package**.
* Extends **Vector**, so it **inherits synchronized methods**.
* Considered **legacy**, but still widely used.

**Key Points:**

* Stack is **synchronized**, thread-safe but slower than modern alternatives.
* **Generic support** since Java 5 (`Stack<Integer>`).

---

## 3. Stack Core Methods

| Method             | Description                                        |
| ------------------ | -------------------------------------------------- |
| `push(E item)`     | Adds element to top of stack                       |
| `pop()`            | Removes and returns top element                    |
| `peek()`           | Returns top element without removing               |
| `empty()`          | Checks if stack is empty                           |
| `search(Object o)` | Returns 1-based position from top, -1 if not found |

---

## 4. Stack Example

```java
import java.util.Stack;

public class StackDemo {
    public static void main(String[] args) {
        Stack<String> stack = new Stack<>();

        // Push elements
        stack.push("A");
        stack.push("B");
        stack.push("C");

        System.out.println("Stack: " + stack); // [A, B, C]

        // Peek top
        System.out.println("Top element: " + stack.peek()); // C

        // Pop elements
        System.out.println("Popped: " + stack.pop()); // C
        System.out.println("Popped: " + stack.pop()); // B

        // Check if empty
        System.out.println("Is stack empty? " + stack.empty()); // false
    }
}
```

**Why this syntax?**

1. `Stack<String> stack = new Stack<>();`

   * Uses **generic** for type safety.
   * Stack is instantiated as a class object.
2. `push()` → adds element on top.
3. `pop()` → removes and returns top element.
4. `peek()` → reads top element without removal.
5. `empty()` → checks if stack has elements.

---

## 5. Performance

| Operation | Time Complexity |
| --------- | --------------- |
| push      | O(1)            |
| pop       | O(1)            |
| peek      | O(1)            |
| search    | O(n)            |

✅ Efficient for **LIFO operations**, but **slower than ArrayDeque** for non-threaded use because of synchronization.

---

## 6. Modern Recommended Alternative – ArrayDeque

* **ArrayDeque** is recommended over Stack for **non-threaded applications**.
* Provides **push, pop, peek** methods similar to Stack.
* Faster because **unsynchronized**.

### 6.1 ArrayDeque Example

```java
import java.util.ArrayDeque;
import java.util.Deque;

public class ArrayDequeStackDemo {
    public static void main(String[] args) {
        Deque<String> stack = new ArrayDeque<>();

        // Push elements
        stack.push("A");
        stack.push("B");
        stack.push("C");

        // Pop elements
        while (!stack.isEmpty()) {
            System.out.println(stack.pop());
        }
    }
}
```

**Advantages:**

1. Faster than Stack (unsynchronized).
2. Provides **stack and queue operations** in one class.
3. Resizable dynamically, like ArrayList.

---

## 7. Stack vs ArrayDeque (for LIFO)

| Feature       | Stack            | ArrayDeque       |
| ------------- | ---------------- | ---------------- |
| Thread safety | Synchronized     | Not synchronized |
| Performance   | Slower           | Faster           |
| Methods       | push, pop, peek  | push, pop, peek  |
| Legacy        | Yes              | No               |
| Use Case      | Thread-safe LIFO | Modern LIFO      |

---

## 8. Additional Stack Concepts

1. **Expression Evaluation using Stack**

```java
// Evaluate postfix expression: "231*+9-"
// Steps: push operands, pop 2 for operator, compute, push result
```

2. **Backtracking with Stack**

   * Undo operations, DFS traversal in trees or graphs.

3. **Nested Stack Example (Generic)**

```java
Stack<Stack<Integer>> matrixStack = new Stack<>();
```

* Stack can store **another stack or any object** for advanced data structures.

---

## 9. Best Practices

1. Use **ArrayDeque** instead of Stack for non-threaded applications.
2. Always use **Generics** for type safety.
3. Use **peek()** before pop() to avoid **EmptyStackException**.
4. Use Stack for **thread-safe legacy code** if needed.
5. Avoid using **Vector methods** directly when using Stack.

---

## 10. Summary

* **Stack** = LIFO data structure.
* **push()** → insert on top, **pop()** → remove top, **peek()** → read top.
* **Stack class** is legacy but thread-safe.
* **ArrayDeque** is the modern, faster alternative.
* Use **Stack** in **expression evaluation, backtracking, undo/redo**.

---

If you want, we can next **cover Java Collections Utility classes** like **Collections and Arrays**, including **sorting, searching, reversing, shuffling, synchronized collections**, which are extremely useful for **Java developers and core learners**.

Do you want me to continue with **Collections utility class** next?
