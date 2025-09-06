Perfect 👍 — You want a **brief but clear foundation of OOP in Java** before diving deep into each concept. I’ll give you a **core overview** that sets the stage for deeper study.

Save this as:

```
Java-Core/08_OOP_Overview.md
```

---

# 🔑 Object-Oriented Programming (OOP) in Java — Overview

Java is a **pure Object-Oriented Programming Language** (except for primitive types).
OOP helps in **organizing code into reusable, logical units**.

The **four pillars** of OOP are:

---

## 1. Encapsulation (Data Hiding)

* **Definition**: Wrapping **data (variables)** and **methods (functions)** together in a single unit (class).
* Protects data from unauthorized access.
* Achieved using **access modifiers** (`private`, `public`, etc.) + **getters/setters**.

👉 Example:

```java
class Student {
    private String name;   // hidden data
    private int age;

    // getter
    public String getName() {
        return name;
    }

    // setter
    public void setName(String name) {
        this.name = name;
    }
}
```

✔️ **Advantage**: Controlled access, better security.

---

## 2. Inheritance (Reusability)

* **Definition**: Acquiring properties and behavior of one class into another.
* Achieved using the **`extends` keyword**.
* Promotes **code reusability**.

👉 Example:

```java
class Animal {
    void eat() {
        System.out.println("Animal is eating");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("Dog is barking");
    }
}
```

✔️ **Dog** inherits `eat()` from **Animal**.

---

## 3. Polymorphism (Many Forms)

* **Definition**: One thing can behave in **different ways**.
* Two types:

  1. **Compile-time Polymorphism (Method Overloading)**

     * Same method name, different parameter list.
  2. **Runtime Polymorphism (Method Overriding)**

     * Child class provides its own implementation of a parent method.

👉 Example:

```java
// Overloading
class MathUtils {
    int add(int a, int b) { return a + b; }
    double add(double a, double b) { return a + b; }
}

// Overriding
class Animal {
    void sound() { System.out.println("Animal sound"); }
}
class Dog extends Animal {
    void sound() { System.out.println("Bark"); } // override
}
```

✔️ Same method, different forms.

---

## 4. Abstraction (Hiding Implementation)

* **Definition**: Showing only **essential details** and hiding implementation.
* Achieved using:

  * **Abstract classes** (`abstract` keyword)
  * **Interfaces** (`interface` keyword)

👉 Example:

```java
abstract class Vehicle {
    abstract void start(); // abstract method (no body)
}

class Car extends Vehicle {
    void start() {
        System.out.println("Car starts with key");
    }
}
```

✔️ User sees **what it does**, not **how it does**.

---

## 5. Class & Object (Foundation of OOP)

* **Class** = Blueprint / template.
* **Object** = Real-world instance of a class.

👉 Example:

```java
class Car {
    String color;
    void drive() { System.out.println("Driving..."); }
}

public class Demo {
    public static void main(String[] args) {
        Car c1 = new Car();   // object
        c1.color = "Red";
        c1.drive();
    }
}
```

---

## 6. Additional OOP Concepts in Java

* **Constructors** → Special methods for object initialization.
* **this & super keywords** → Refers to current object / parent class.
* **Access Modifiers** → (`private`, `default`, `protected`, `public`) control visibility.
* **final keyword** → Prevents modification (final variable, method, class).

---

# ✅ Summary for Beginners

* **Encapsulation** → Data hiding (security).
* **Inheritance** → Reusability.
* **Polymorphism** → Many forms (overloading, overriding).
* **Abstraction** → Hides implementation (abstract class/interface).
* **Class & Object** → Core building blocks.

---

👉 Next Step: We can go **in-depth one by one**.
Would you like me to start with **Encapsulation (detailed with diagrams + real-world analogy + code examples)**?
