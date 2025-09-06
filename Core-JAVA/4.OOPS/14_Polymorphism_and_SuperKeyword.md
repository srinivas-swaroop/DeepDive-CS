Perfect! Now we’re diving into **Polymorphism + `super` keyword** — two concepts that are tightly coupled in **Java OOP**. I’ll give a **very detailed explanation**, with **examples, rules, use cases, and best practices** for core learners and developers.

Save as:

```
Java-Core/14_Polymorphism_and_SuperKeyword.md
```

---

# 🔄 Polymorphism & `super` Keyword in Java

---

## 1. Polymorphism in Java

### 🔹 Definition

* **Polymorphism** = “**Many forms**”
* An entity (object, method, operator) behaves differently in different situations.
* In Java, it allows **one interface, method, or class reference** to work with **multiple forms**.

Polymorphism in Java is of **two types**:

1. **Compile-Time Polymorphism (Method Overloading)**
2. **Runtime Polymorphism (Method Overriding)**

---

## 2. Compile-Time Polymorphism (Method Overloading)

### 🔹 Key Points

* **Same method name** but **different parameters** (number, type, or sequence).
* **Return type can be same or different** (but overloading is based on parameters, not return type).
* Resolved at **compile time**.

### 🔹 Example:

```java
class Calculator {
    int add(int a, int b) {
        return a + b;
    }

    double add(double a, double b) {
        return a + b;
    }

    int add(int a, int b, int c) {
        return a + b + c;
    }
}

public class Demo {
    public static void main(String[] args) {
        Calculator calc = new Calculator();
        System.out.println(calc.add(5, 10));        // 15
        System.out.println(calc.add(5.5, 4.5));     // 10.0
        System.out.println(calc.add(1, 2, 3));      // 6
    }
}
```

✅ Overloading increases **code readability and reusability**.

---

## 3. Runtime Polymorphism (Method Overriding)

### 🔹 Key Points

* Subclass provides **its own implementation** of a method from parent class.
* Resolved at **runtime** using **dynamic method dispatch**.
* Rules:

  * Same method name, parameters, and return type (or covariant return type).
  * Cannot reduce visibility.
  * `private` methods cannot be overridden.
  * Static methods cannot be overridden (can be hidden).

### 🔹 Example:

```java
class Animal {
    void sound() { System.out.println("Animal sound"); }
}

class Dog extends Animal {
    @Override
    void sound() { System.out.println("Dog barks"); }
}

class Cat extends Animal {
    @Override
    void sound() { System.out.println("Cat meows"); }
}

public class Demo {
    public static void main(String[] args) {
        Animal a1 = new Dog();
        Animal a2 = new Cat();

        a1.sound(); // Dog barks
        a2.sound(); // Cat meows
    }
}
```

---

### 🔹 Benefits of Polymorphism

* ✅ Code Reusability → same method name, different functionality.
* ✅ Maintainability → easier to extend.
* ✅ Flexibility → one reference type can refer to multiple object types.

---

## 4. The `super` Keyword

The `super` keyword is used to **refer to the parent class members (variables, methods, constructors)**.

### 4.1 Uses of `super`

---

#### (a) Access Parent Class Variables

```java
class Animal {
    String type = "Animal";
}

class Dog extends Animal {
    String type = "Dog";

    void printType() {
        System.out.println(type);        // Dog
        System.out.println(super.type);  // Animal
    }
}
```

---

#### (b) Call Parent Class Methods

```java
class Animal {
    void eat() { System.out.println("Animal eats"); }
}

class Dog extends Animal {
    void eat() {
        System.out.println("Dog eats");
    }

    void show() {
        eat();       // Dog eats
        super.eat(); // Animal eats
    }
}
```

---

#### (c) Call Parent Class Constructor

* **Constructor chaining** → call parent constructor using `super()`.

```java
class Animal {
    Animal() {
        System.out.println("Animal constructor");
    }
}

class Dog extends Animal {
    Dog() {
        super(); // call parent constructor
        System.out.println("Dog constructor");
    }
}

public class Demo {
    public static void main(String[] args) {
        Dog d = new Dog();
    }
}

// Output:
// Animal constructor
// Dog constructor
```

* Note: `super()` must be **the first statement in the constructor**.

---

### 4.2 Real-World Analogy

* **Polymorphism** = same word but different meanings in different contexts.

  * Example: “play” → play football, play guitar, play video.
* **super** = referring to parent class like saying *“my parent did this, I’ll extend it”*.

---

### 5. Combining Polymorphism + `super`

```java
class Vehicle {
    void move() { System.out.println("Vehicle moves"); }
}

class Car extends Vehicle {
    @Override
    void move() {
        super.move(); // call Vehicle method
        System.out.println("Car moves fast");
    }
}

public class Demo {
    public static void main(String[] args) {
        Car c = new Car();
        c.move();
    }
}

// Output:
// Vehicle moves
// Car moves fast
```

---

### 6. Best Practices

✅ Use **polymorphism** for flexibility and clean code.
✅ Always annotate overridden methods with `@Override`.
✅ Use **super** to **avoid code duplication** and call parent functionality.
✅ Avoid deep inheritance hierarchies; prefer **composition** if possible.
✅ Use **constructor chaining** for proper object initialization.

---

# ✅ Summary

* **Polymorphism** → one name, many forms.

  * Compile-time → method overloading.
  * Runtime → method overriding.
* **super keyword** → access parent members (variables, methods, constructors).
* Together → enables **code reuse, flexibility, and clean OOP design**.

---

If you want, next I can cover **Abstract Classes & Interfaces** in full detail — because they naturally follow polymorphism and are essential for **Java developers**.

Do you want me to continue with that?
