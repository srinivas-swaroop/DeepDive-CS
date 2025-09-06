Perfect! Let’s do a **full deep dive into Java Interfaces**, which are essential for **OOP design, abstraction, and multiple inheritance**. I’ll provide **definitions, syntax, examples, rules, new Java features, best practices, and real-world analogies** suitable for **core Java learners and developers**.

Save as:

```
Java-Core/16_Interfaces.md
```

---

# 🧩 Java Interfaces – Detailed Explanation

---

## 1. What is an Interface in Java?

* An **interface** in Java is a **reference type** (like a class) that is used to define **a contract** for classes.
* It contains **abstract methods** (method signatures) that **must be implemented** by the class implementing the interface.
* Interfaces **cannot be instantiated** directly.

**Key Idea:**

> “An interface specifies what a class must do, but not how it does it.”

---

## 2. Syntax

```java
interface Vehicle {
    int MAX_SPEED = 120; // constant (public static final by default)
    void start();         // abstract method (public abstract by default)
    void stop();
}
```

**Notes:**

* Fields are **public static final** by default.
* Methods are **public abstract** by default (before Java 8).

---

## 3. Implementing an Interface

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
        v.start(); // Car starts
        v.stop();  // Car stops
        System.out.println("Max speed: " + Vehicle.MAX_SPEED); // 120
    }
}
```

✅ Note: `implements` keyword is used for classes to inherit interface behavior.

---

## 4. Key Features of Interfaces

1. **Multiple Inheritance Support**

   * Java **does not support multiple inheritance with classes**, but **interfaces allow it**.

```java
interface Flyable { void fly(); }
interface Swimable { void swim(); }

class Duck implements Flyable, Swimable {
    public void fly() { System.out.println("Duck flies"); }
    public void swim() { System.out.println("Duck swims"); }
}
```

2. **No Constructors**

   * Interfaces **cannot have constructors**, so you **cannot instantiate them** directly.

3. **All Methods Are Abstract by Default** *(Java < 8)*

4. **Static and Default Methods (Java 8+)**

   * **Default methods** → concrete methods inside interfaces.
   * **Static methods** → belong to the interface itself.

```java
interface Vehicle {
    default void fuel() {
        System.out.println("Refueling vehicle");
    }

    static void companyInfo() {
        System.out.println("Interface: Vehicles Inc.");
    }
}

class Bike implements Vehicle {}

public class Demo {
    public static void main(String[] args) {
        Bike b = new Bike();
        b.fuel(); // Refueling vehicle
        Vehicle.companyInfo(); // Interface: Vehicles Inc.
    }
}
```

---

## 5. Java 9 Features (Private Methods in Interfaces)

* Private methods can be defined in interfaces to **avoid code duplication in default methods**.

```java
interface Vehicle {
    private void internalCheck() {
        System.out.println("Performing internal check");
    }

    default void startVehicle() {
        internalCheck();
        System.out.println("Vehicle started");
    }
}
```

---

## 6. Rules of Interfaces

1. A class **must implement all abstract methods** of an interface.
2. A class can **implement multiple interfaces**.
3. An interface **can extend multiple interfaces**.
4. Fields are **public static final** by default.
5. Methods are **public abstract** by default (before Java 8).
6. You **cannot create an object** of an interface directly.

---

## 7. Interface Inheritance

### 7.1 Interface Extending Interface

```java
interface A { void methodA(); }
interface B extends A { void methodB(); }

class Test implements B {
    public void methodA() { System.out.println("Method A"); }
    public void methodB() { System.out.println("Method B"); }
}
```

✅ A class implementing `B` must **implement all methods from A and B**.

---

### 7.2 Multiple Interfaces in a Class

```java
interface Flyable { void fly(); }
interface Swimable { void swim(); }

class Duck implements Flyable, Swimable {
    public void fly() { System.out.println("Duck flies"); }
    public void swim() { System.out.println("Duck swims"); }
}
```

---

## 8. Real-World Analogy

* **Interface** = contract or job description.
* **Class** = employee implementing the contract.
* You only care about **what the employee does** (methods), not **how they do it**.

Example:

* `Flyable` → any class that flies: Bird, Airplane, Drone
* `Swimable` → any class that swims: Fish, Duck, Submarine

---

## 9. Advantages of Using Interfaces

* ✅ Achieves **100% abstraction**.
* ✅ Supports **multiple inheritance** safely.
* ✅ Improves **loose coupling**.
* ✅ Promotes **code reusability** and **polymorphism**.
* ✅ Essential for **API design and framework development**.

---

## 10. Interface vs Abstract Class

| Feature     | Interface                       | Abstract Class          |
| ----------- | ------------------------------- | ----------------------- |
| Inheritance | Multiple via implements         | Single (extends)        |
| Methods     | abstract + default + static     | abstract + concrete     |
| Fields      | public static final (constants) | instance or static      |
| Constructor | ❌                               | ✅                       |
| Use-case    | Unrelated classes behavior      | Closely related classes |

---

## 11. Best Practices

* Use **interfaces for capabilities**: `Flyable`, `Swimable`, `Playable`.
* Use **abstract classes for “is-a” relationship**.
* Always implement **all methods** in the implementing class.
* Prefer **default methods** instead of changing old interface methods (Java 8+).
* Combine **interfaces + polymorphism** for flexible design.

---

## 12. Summary

* **Interface** = contract defining **what a class should do**, without specifying **how**.
* Allows **multiple inheritance**, **polymorphism**, and **100% abstraction**.
* Java 8+ features: **default and static methods**.
* Java 9+ features: **private methods**.
* Interfaces are **core for designing modular, scalable Java applications**.

---

If you want, the next topic can be **Exception Handling in Java** in full depth — covering **try-catch, finally, throw, throws, checked/unchecked exceptions, custom exceptions** — which is crucial for **Java developers**.

Do you want me to continue with that?
