Perfect 👌 — You’ve already mastered **Comparable**, now let’s dive into its sibling: **Comparator**.
This is **super important in core Java**, because most real-world sorting/ordering is done with **Comparator**.
I’ll give you **theory → syntax → multiple implementations → advanced use cases → finally a crisp comparison table with Comparable**.

---

# 🔹 Comparator in Java (Full Guide)

---

## 1. What is Comparator?

* `Comparator` is an **interface** in `java.util` package.
* It is used to define **custom ordering** of objects.
* Unlike `Comparable` (which defines *one natural order* inside the class itself), `Comparator` lets you create **multiple sorting logics** outside the class.

👉 **Signature**:

```java
public interface Comparator<T> {
    int compare(T o1, T o2);
    boolean equals(Object obj); // optional, rarely overridden
}
```

---

## 2. Behavior of `compare()`

The method `compare(o1, o2)` must return:

* **Negative** → `o1 < o2`
* **Zero** → `o1 == o2`
* **Positive** → `o1 > o2`

Same as `Comparable`, but here you compare **two objects passed into the method**, not `this` and `other`.

---

## 3. Why Comparator?

* Allows **multiple sorting strategies** for the same class.
* Keeps sorting logic **outside the class**, so class stays clean.
* Can sort classes that you **cannot modify** (e.g., library classes).
* Used in real-world applications where sorting is dynamic (by name, age, salary, etc.).

---

## 4. Basic Implementation Example

### (A) Classic Anonymous Class

```java
import java.util.*;

class Student {
    int id;
    String name;
    int marks;

    Student(int id, String name, int marks) {
        this.id = id;
        this.name = name;
        this.marks = marks;
    }

    @Override
    public String toString() {
        return id + " - " + name + " - " + marks;
    }
}

public class Test {
    public static void main(String[] args) {
        List<Student> list = new ArrayList<>();
        list.add(new Student(3, "Ravi", 85));
        list.add(new Student(1, "Ankit", 90));
        list.add(new Student(2, "Sita", 78));

        // Comparator by marks
        Comparator<Student> marksComparator = new Comparator<Student>() {
            public int compare(Student s1, Student s2) {
                return Integer.compare(s1.marks, s2.marks);
            }
        };

        Collections.sort(list, marksComparator);
        System.out.println(list);
    }
}
```

**Output:**

```
2 - Sita - 78
3 - Ravi - 85
1 - Ankit - 90
```

---

### (B) Using Lambda (Java 8+)

```java
Collections.sort(list, (s1, s2) -> Integer.compare(s1.marks, s2.marks));
```

---

### (C) Comparator.comparing() (Java 8+)

```java
list.sort(Comparator.comparing(s -> s.name));
```

---

### (D) Comparator with Method Reference

```java
list.sort(Comparator.comparing(Student::getName));
```

---

### (E) Reverse Order

```java
list.sort(Comparator.comparingInt(s -> s.marks).reversed());
```

---

### (F) Multiple Fields (Chaining)

```java
list.sort(
    Comparator.comparing(Student::getMarks)
              .thenComparing(Student::getName)
);
```

👉 First sort by marks, if equal → sort by name.

---

## 5. Special Implementations

1. **Custom Comparator Class**

```java
class NameComparator implements Comparator<Student> {
    public int compare(Student s1, Student s2) {
        return s1.name.compareTo(s2.name);
    }
}
```

Use:

```java
Collections.sort(list, new NameComparator());
```

---

2. **Comparing with Null Handling**

```java
list.sort(Comparator.nullsLast(Comparator.comparing(Student::getName)));
```

---

3. **Comparing Primitive Fields**

```java
list.sort(Comparator.comparingInt(s -> s.marks));
```

(Similar methods exist: `comparingDouble`, `comparingLong`.)

---

4. **Comparing Multiple with Complex Rules**

```java
Comparator<Student> customComparator = (s1, s2) -> {
    if (s1.marks != s2.marks)
        return Integer.compare(s1.marks, s2.marks);
    return s1.name.compareTo(s2.name); // tie-breaker
};
list.sort(customComparator);
```

---

## 6. Where Comparator is Used in Java

* `Collections.sort(list, comparator)`
* `Arrays.sort(array, comparator)`
* Priority-based structures (`PriorityQueue`, `TreeSet`, `TreeMap`)
* Database-style sorting (dynamic sorting strategies)

---

## 7. Common Mistakes

❌ Returning only `0` or `1` (not correct).
❌ Forgetting tie-breakers in multi-field sorting.
❌ Writing too many nested `if` conditions (better use `Comparator.comparing().thenComparing()`).

---

# 🔹 Comparable vs Comparator (Table)

| Feature           | Comparable                                                   | Comparator                                                                |
| ----------------- | ------------------------------------------------------------ | ------------------------------------------------------------------------- |
| Package           | `java.lang`                                                  | `java.util`                                                               |
| Method            | `compareTo(T o)`                                             | `compare(T o1, T o2)`                                                     |
| Used for          | **Natural ordering** (default, single order)                 | **Custom ordering** (multiple strategies)                                 |
| Defined in        | Inside the class itself                                      | Outside the class (separate class, lambda, or method reference)           |
| Modifies class?   | Yes (class must implement it)                                | No (can work on existing/unmodifiable classes)                            |
| Multiple sorting? | No (only one natural order)                                  | Yes (define as many comparators as needed)                                |
| Example           | `Collections.sort(list)`                                     | `Collections.sort(list, comparator)`                                      |
| Preferred when    | Class has a single, natural order (like `String`, `Integer`) | You want flexibility, multiple sorting logics, or cannot modify the class |

---

# 🔑 Takeaways

* **Use Comparable** → when you want a **default natural order** of your class.
* **Use Comparator** → when you want **different sorting logics** or don’t own the class.
* Modern Java (8+) makes Comparator very powerful with `Comparator.comparing()`, chaining, and method references.

---

👉 Now, would you like me to **show a real-world project-like example** where we sort employees with multiple rules (salary → name → age) using both **Comparable and Comparator**, so you see the contrast in action?
