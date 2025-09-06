Perfect! Now we’re diving into **Abstraction in Java** — another core OOP pillar, essential for building **flexible and modular applications**. I’ll give a **very detailed explanation**, including **abstract classes, abstract methods, interfaces, rules, examples, real-world analogies, and best practices**.

Save as:

```
Java-Core/15_Abstraction.md
```

---

# 🧩 Abstraction in Java (Detailed Explanation)

---

## 1. What is Abstraction?

* **Abstraction** = Hiding **implementation details** and showing only **essential functionality** to the user.
* Helps in **reducing complexity** and **increasing modularity**.

**Analogy:**

* You use a **TV remote** without knowing the internal circuit. You only see **buttons** and **functions** (abstracted details).

---

## 2. Achieving Abstraction in Java

There are **two ways** to achieve abstraction:

1. **Abstract Classes**
2. **Interfaces**

---

## 3. Abstract Classes

### 3.1 Definition

* A class declared with the **`abstract` keyword**.
* Can have:

  * **Abstract methods** (no body)
  * **Concrete methods** (with body)
* Cannot create **direct instances** of abstract class.

### 3.2 Syntax

```java
abstract class Animal {
    abstract void sound(); // abstract method

    void eat() {           // concrete method
        System.out.println("Animal eats");
    }
}
```

---

### 3.3 Rules

1. Abstract class **cannot be instantiated** directly.
2. Abstract method must be implemented by **subclass**.
3. A class with **at least one abstract method** must be declared abstract.
4. Abstract class **can have constructors** (used in subclass).
5. Can have **static, final, non-final methods and variables**.

---

### 3.4 Example

```java
abstract class Animal {
    abstract void sound(); // must be implemented by subclass

    void eat() {
        System.out.println("Animal eats");
    }
}

class Dog extends Animal {
    @Override
    void sound() {
        System.out.println("Dog barks");
    }
}

public class Demo {
    public static void main(String[] args) {
        Animal a = new Dog(); // polymorphic reference
        a.eat();   // inherited concrete method
        a.sound(); // overridden abstract method
    }
}
```

---

### 3.5 Abstract Class vs Interface

| Feature              | Abstract Class             | Interface                    |
| -------------------- | -------------------------- | ---------------------------- |
| Multiple Inheritance | ❌ (single)                 | ✅ (via implements)           |
| Methods              | abstract + concrete        | Java 8+: default + abstract  |
| Variables            | instance or static         | static final (constants)     |
| Constructor          | ✅                          | ❌                            |
| Access Modifiers     | public, protected, private | public (all methods default) |

---

## 4. Interfaces

### 4.1 Definition

* **Interface** = 100% abstraction (before Java 8).
* Can only contain:

  * **abstract methods**
  * **constants** (`static final`)

### 4.2 Syntax

```java
interface Vehicle {
    int MAX_SPEED = 120; // constant

    void start(); // abstract method
    void stop();
}
```

---

### 4.3 Implementing Interface

```java
class Car implements Vehicle {
    @Override
    public void start() {
        System.out.println("Car starts");
    }

    @Override
    public void stop() {
        System.out.println("Car stops");
    }
}

public class Demo {
    public static void main(String[] args) {
        Vehicle v = new Car();
        v.start();
        v.stop();
        System.out.println("Max speed: " + Vehicle.MAX_SPEED);
    }
}
```

---

### 4.4 Multiple Inheritance via Interface

```java
interface Flyable {
    void fly();
}

interface Swimable {
    void swim();
}

class Duck implements Flyable, Swimable {
    public void fly() { System.out.println("Duck flies"); }
    public void swim() { System.out.println("Duck swims"); }
}
```

✅ This allows **hybrid inheritance** safely.

---

## 5. Abstract Class vs Interface Deep Comparison

| Feature               | Abstract Class                           | Interface                                          |
| --------------------- | ---------------------------------------- | -------------------------------------------------- |
| Inheritance type      | Single inheritance                       | Multiple inheritance allowed                       |
| Constructors          | Yes                                      | No                                                 |
| Method implementation | Can have concrete methods                | Java 8+: default, static methods only              |
| Fields                | Any type                                 | `public static final` constants                    |
| Accessibility         | Any (private, protected, public)         | public only                                        |
| Use-case              | “Is-a” relationship, partial abstraction | Multiple unrelated classes sharing common behavior |

---

## 6. Real-World Analogy

* **Abstract Class** → Blueprint for cars: “All cars have engine + wheels, but type of engine may differ”.
* **Interface** → Capability: “Can fly, can swim, can drive”.

  * A duck **can fly and swim** → implements multiple interfaces.
* **Polymorphic reference** → “I only know the object is an Animal/Vehicle, I don’t care about actual type”.

---

## 7. Best Practices

✅ Use **abstract class** when classes are closely related and share some implementation.
✅ Use **interfaces** to define **common behavior across unrelated classes**.
✅ Always **annotate overridden methods with `@Override`**.
✅ Combine **polymorphism + abstraction** for flexible and maintainable design.
✅ Avoid empty abstract classes or interfaces — they should provide meaningful abstraction.

---

## 8. Summary

* **Abstraction** → hide details, show functionality.
* **Abstract Class** → partial abstraction, can have concrete + abstract methods.
* **Interface** → full abstraction, used for multiple inheritance.
* **Polymorphism + Abstraction** → allows flexible, scalable, maintainable code.
* Use **abstract classes for closely related objects** and **interfaces for common behavior across unrelated classes**.

---

If you want, next I can cover **Exception Handling in Java** in **full depth**, including **try-catch, finally, throw, throws, custom exceptions, checked & unchecked exceptions**, which is crucial for **core Java developers**.

Do you want me to continue with that?
