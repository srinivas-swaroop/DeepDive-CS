Perfect 👌 — You want a **detailed breakdown of Java Classes, Objects, Attributes, and Methods**. This is the **foundation of OOP in Java**, so I’ll go step by step with **concepts, code examples, rules, and best practices**.

Save this as:

```
Java-Core/09_Classes_Objects_Methods.md
```

---

# 📘 Java Classes, Objects, Attributes, and Methods

In Java, everything in OOP revolves around **classes** and **objects**.
Let’s explore them deeply.

---

## 1. Class

### 🔹 Definition

* A **class** is a **blueprint/template** for creating objects.
* It defines **attributes (variables)** and **methods (functions)**.

👉 Example:

```java
class Car {
    // attributes (fields/properties)
    String color;
    int speed;

    // methods (functions/behavior)
    void drive() {
        System.out.println("Car is driving...");
    }
}
```

✔️ A **class** does not take memory until an **object** is created.

---

## 2. Object

### 🔹 Definition

* An **object** is an **instance of a class**.
* Each object gets its own copy of **non-static attributes**, but shares **static attributes**.

👉 Example:

```java
public class Demo {
    public static void main(String[] args) {
        // Creating objects
        Car car1 = new Car();  
        Car car2 = new Car();

        // Assign attributes
        car1.color = "Red";
        car1.speed = 120;

        car2.color = "Blue";
        car2.speed = 150;

        // Call methods
        car1.drive(); // Car is driving...
        car2.drive(); // Car is driving...
    }
}
```

✔️ `car1` and `car2` are **different objects** with their own data.

---

## 3. Attributes (Fields / Properties)

* Attributes are **variables inside a class** that store object data.
* Types of attributes:

  1. **Instance variables (non-static)** → unique for each object.
  2. **Class variables (static)** → shared among all objects.

👉 Example:

```java
class Student {
    // Instance variable
    String name;

    // Class variable
    static String college = "VIT";
}
```

---

## 4. Methods

### 🔹 Definition

* A **method** is a block of code that performs an action.
* Defines the **behavior** of the object.

👉 Example:

```java
class Calculator {
    int add(int a, int b) {
        return a + b;
    }

    void greet() {
        System.out.println("Hello, welcome to Calculator!");
    }
}
```

---

### 4.1 Method Types

1. **Instance Methods** → require an object to call.

   ```java
   Calculator c = new Calculator();
   System.out.println(c.add(5, 3)); // 8
   ```

2. **Static Methods** → belong to the class, called with `ClassName.method()`.

   ```java
   class MathUtils {
       static int square(int n) {
           return n * n;
       }
   }

   System.out.println(MathUtils.square(4)); // 16
   ```

---

### 4.2 Method Parameters and Return Types

* Methods can take **parameters** and **return values**.

```java
class Greeter {
    String greet(String name) {
        return "Hello, " + name + "!";
    }
}

public class Demo {
    public static void main(String[] args) {
        Greeter g = new Greeter();
        System.out.println(g.greet("Swaroop")); // Hello, Swaroop!
    }
}
```

---

### 4.3 Method Overloading

* Same method name, but **different parameter lists**.
* Helps in creating **multiple versions** of a method.

```java
class MathUtils {
    int add(int a, int b) { return a + b; }
    double add(double a, double b) { return a + b; }
}
```

---

## 5. Constructors

* **Special methods** used to initialize objects.
* Same name as the class.
* No return type.

👉 Example:

```java
class Student {
    String name;
    int age;

    // Constructor
    Student(String n, int a) {
        name = n;
        age = a;
    }

    void display() {
        System.out.println(name + " - " + age);
    }
}

public class Demo {
    public static void main(String[] args) {
        Student s1 = new Student("Swaroop", 21);
        Student s2 = new Student("Rahul", 22);

        s1.display();
        s2.display();
    }
}
```

---

## 6. Access Modifiers

* Define **visibility** of attributes and methods.

| Modifier    | Accessible within Class | Package | Subclass | World |
| ----------- | ----------------------- | ------- | -------- | ----- |
| `private`   | ✅                       | ❌       | ❌        | ❌     |
| `default`   | ✅                       | ✅       | ❌        | ❌     |
| `protected` | ✅                       | ✅       | ✅        | ❌     |
| `public`    | ✅                       | ✅       | ✅        | ✅     |

---

## 7. Real-World Analogy

Think of a **Class** as a **blueprint of a house**.

* **Class** = House blueprint.
* **Object** = Actual house built from blueprint.
* **Attributes** = House color, size, number of rooms.
* **Methods** = House actions like openDoor(), switchOnLight().

---

## 8. Best Practices

✅ Keep attributes **private** (use encapsulation).
✅ Use **meaningful method and class names**.
✅ Prefer **static methods** only for utility/helper logic.
✅ Use **constructors** for proper initialization.

---

# ✅ Summary

* **Class** → Blueprint/template.
* **Object** → Instance of class.
* **Attributes** → Variables inside class (state).
* **Methods** → Functions inside class (behavior).
* **Constructors** → Initialize objects.
* **Access Modifiers** → Control visibility.

---

👉 Next, do you want me to go **deep into Encapsulation (with getters, setters, access modifiers, real-world examples, and diagrams)** as the first major OOP pillar?
