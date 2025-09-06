Awesome 🚀 — you’ve now reached **Access Modifiers + `this` keyword**, two very important building blocks for understanding how Java manages **object data + method access**.

I’ll give you a **detailed explanation with tables, examples, and best practices**.

Save as:

```
Java-Core/10_AccessModifiers_and_ThisKeyword.md
```

---

# 🔑 Java Access Modifiers & `this` Keyword

---

## 1. Access Modifiers in Java

Access modifiers define **scope (visibility)** of **classes, attributes, methods, and constructors**.

### 1.1 Types of Access Modifiers

| Modifier                   | Within Class | Same Package | Subclass (different package) | Everywhere |
| -------------------------- | ------------ | ------------ | ---------------------------- | ---------- |
| **private**                | ✅ Yes        | ❌ No         | ❌ No                         | ❌ No       |
| **default** *(no keyword)* | ✅ Yes        | ✅ Yes        | ❌ No                         | ❌ No       |
| **protected**              | ✅ Yes        | ✅ Yes        | ✅ Yes                        | ❌ No       |
| **public**                 | ✅ Yes        | ✅ Yes        | ✅ Yes                        | ✅ Yes      |

---

### 1.2 Private

* Accessible only **within the same class**.
* Used to **encapsulate data**.

```java
class Student {
    private String name; // private

    public void setName(String n) {
        name = n;
    }

    public String getName() {
        return name;
    }
}

public class Demo {
    public static void main(String[] args) {
        Student s = new Student();
        s.setName("Swaroop");
        System.out.println(s.getName()); // Swaroop
    }
}
```

---

### 1.3 Default (Package-Private)

* No keyword = accessible **only within the same package**.

```java
// File1.java (same package)
class Dog {
    void bark() {
        System.out.println("Bark!");
    }
}

// File2.java (same package)
public class Demo {
    public static void main(String[] args) {
        Dog d = new Dog();  
        d.bark(); // works (same package)
    }
}
```

⚠️ If `Dog` were in another package → ❌ Compile-time error.

---

### 1.4 Protected

* Accessible in **same package** and in **subclasses (inheritance)**.

```java
package animals;

public class Animal {
    protected void eat() {
        System.out.println("Animal is eating...");
    }
}
```

```java
package pets;
import animals.Animal;

class Dog extends Animal {
    void action() {
        eat(); // ✅ accessible (protected + subclass)
    }
}
```

---

### 1.5 Public

* Accessible **everywhere**.

```java
public class Calculator {
    public int add(int a, int b) {
        return a + b;
    }
}
```

---

### 1.6 Summary Table

| Modifier  | Class | Package | Subclass | World |
| --------- | ----- | ------- | -------- | ----- |
| private   | ✅     | ❌       | ❌        | ❌     |
| default   | ✅     | ✅       | ❌        | ❌     |
| protected | ✅     | ✅       | ✅        | ❌     |
| public    | ✅     | ✅       | ✅        | ✅     |

---

## 2. `this` Keyword in Java

The **`this` keyword** is a reference to the **current object** (the object whose method/constructor is being executed).

### 2.1 Uses of `this`

---

#### (a) Referring to Current Instance Variables

When local variable **name** shadows instance variable **name**, use `this`.

```java
class Student {
    String name;

    Student(String name) {
        this.name = name; // distinguish local vs instance variable
    }

    void display() {
        System.out.println("Name: " + name);
    }
}

public class Demo {
    public static void main(String[] args) {
        Student s = new Student("Swaroop");
        s.display(); // Name: Swaroop
    }
}
```

---

#### (b) Calling Current Class Methods

```java
class Test {
    void m1() {
        System.out.println("m1 method");
    }

    void m2() {
        this.m1(); // calling m1 using this
    }
}
```

---

#### (c) Calling Current Class Constructors (Constructor Chaining)

```java
class Student {
    String name;
    int age;

    Student(String name) {
        this(name, 18); // calling another constructor
    }

    Student(String name, int age) {
        this.name = name;
        this.age = age;
    }

    void display() {
        System.out.println(name + " - " + age);
    }
}
```

---

#### (d) Passing Current Object as a Parameter

```java
class Student {
    void print(Student s) {
        System.out.println("Object reference passed");
    }

    void call() {
        print(this); // passing current object
    }
}

public class Demo {
    public static void main(String[] args) {
        Student s = new Student();
        s.call();
    }
}
```

---

#### (e) Returning Current Object

```java
class Student {
    Student getObject() {
        return this; // returning current object
    }
}
```

---

## 3. Real-World Analogy

* **Access Modifiers** → Like security levels in a company:

  * `private` = Only you.
  * `default` = Team members.
  * `protected` = Department + interns (subclasses).
  * `public` = Anyone in the world.

* **this keyword** → Like saying *“me/myself”* in real life.

  * “I am calling my own method” → `this.m1()`.
  * “I am giving myself as reference” → `obj.method(this)`.

---

## 4. Best Practices

✅ Always keep fields `private` and expose them via **getters/setters**.
✅ Use `this` to **avoid shadowing confusion** between local and instance variables.
✅ Use `this()` for **constructor chaining** to reduce code duplication.
✅ Avoid unnecessary use of `this` when not required (Java auto-resolves).

---

# ✅ Summary

* **Access Modifiers** control visibility → `private`, `default`, `protected`, `public`.
* **this keyword** refers to the current object.

  * Used for variable disambiguation.
  * To call methods/constructors of current class.
  * To pass/return current object.

---

👉 Do you want me to next go **Encapsulation (deep dive using access modifiers + this keyword + real-world analogy like ATM)** since it directly connects to what we just covered?


Perfect question 👍 — Constructors are **key in Java OOP** since they handle **object initialization**. Many learners only know the basics, but as a developer you should clearly understand the **types of constructors**, how they work, and best practices.

Save this as:

```
Java-Core/11_Constructors_Types.md
```

---

# 🏗️ Constructors in Java (Detailed Guide)

---

## 1. What is a Constructor?

* A **constructor** is a **special method** in Java used to **initialize objects**.
* It has:

  * The **same name as the class**.
  * **No return type** (not even `void`).
* Called **automatically** when an object is created.

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
        s1.display(); // Swaroop - 21
    }
}
```

---

## 2. Types of Constructors in Java

Java supports **two main types of constructors**:

1. **Default Constructor (No-Arg Constructor)**
2. **Parameterized Constructor**

Additionally, Java also allows:
3\. **Copy Constructor** *(not built-in like C++, but can be defined manually)*

---

### 2.1 Default Constructor

* A **no-argument constructor** created by the compiler if you don’t write any constructor.
* Initializes **default values** (`0`, `null`, `false`).

👉 Example:

```java
class Car {
    String model;
    int speed;

    // No constructor written → Compiler creates a default constructor

    void display() {
        System.out.println(model + " - " + speed);
    }
}

public class Demo {
    public static void main(String[] args) {
        Car c = new Car();  // compiler calls default constructor
        c.display(); // null - 0
    }
}
```

🔹 If you write your **own constructor**, Java will **not** provide a default one.

👉 Explicit No-Arg Constructor:

```java
class Car {
    String model;
    int speed;

    // Explicit no-arg constructor
    Car() {
        model = "Unknown";
        speed = 0;
    }

    void display() {
        System.out.println(model + " - " + speed);
    }
}
```

---

### 2.2 Parameterized Constructor

* Constructor with **parameters** to assign custom values during object creation.

👉 Example:

```java
class Car {
    String model;
    int speed;

    Car(String m, int s) {
        model = m;
        speed = s;
    }

    void display() {
        System.out.println(model + " - " + speed);
    }
}

public class Demo {
    public static void main(String[] args) {
        Car c1 = new Car("BMW", 180);
        Car c2 = new Car("Audi", 200);

        c1.display(); // BMW - 180
        c2.display(); // Audi - 200
    }
}
```

✔️ Useful when you want **different objects initialized with different data**.

---

### 2.3 Copy Constructor

* Java doesn’t have a **built-in copy constructor** like C++.
* But you can **define one manually** to create a new object by copying another object.

👉 Example:

```java
class Car {
    String model;
    int speed;

    // Parameterized constructor
    Car(String m, int s) {
        model = m;
        speed = s;
    }

    // Copy constructor
    Car(Car c) {
        this.model = c.model;
        this.speed = c.speed;
    }

    void display() {
        System.out.println(model + " - " + speed);
    }
}

public class Demo {
    public static void main(String[] args) {
        Car c1 = new Car("Tesla", 250);
        Car c2 = new Car(c1); // Copy constructor

        c1.display(); // Tesla - 250
        c2.display(); // Tesla - 250
    }
}
```

✔️ Often used for **cloning objects** safely.

---

## 3. Constructor Overloading

* Java allows **multiple constructors in the same class** (different parameter lists).
* This is called **Constructor Overloading**.

👉 Example:

```java
class Student {
    String name;
    int age;

    // No-arg constructor
    Student() {
        name = "Unknown";
        age = 18;
    }

    // Parameterized constructor
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
        Student s1 = new Student();
        Student s2 = new Student("Swaroop", 21);

        s1.display(); // Unknown - 18
        s2.display(); // Swaroop - 21
    }
}
```

---

## 4. Constructor vs Method

| Feature               | Constructor                    | Method                        |
| --------------------- | ------------------------------ | ----------------------------- |
| Name                  | Same as class                  | Any valid name                |
| Return type           | No return type                 | Has return type (can be void) |
| Called automatically? | ✅ Yes (when object is created) | ❌ No (must call explicitly)   |
| Purpose               | Initialize object              | Define behavior/actions       |

---

## 5. Real-World Analogy

Think of a **class as a building plan**.

* A **constructor** is like a **construction process** → it sets up the house with paint, furniture, etc.
* A **method** is like the **daily activities in the house** (open door, switch on lights).

---

## 6. Best Practices

✅ Always initialize variables inside constructors to avoid **null values**.
✅ Use **constructor overloading** for flexibility.
✅ Prefer **constructor chaining** with `this()` to avoid code duplication.
✅ Define a **copy constructor** if objects need to be cloned safely.
✅ Don’t put **business logic** in constructors (keep them simple).

---

# ✅ Summary

* **Default Constructor** → Created by compiler if no constructor is written.
* **Parameterized Constructor** → Allows passing values during object creation.
* **Copy Constructor** → Manually defined to copy another object.
* **Constructor Overloading** → Multiple constructors with different parameter lists.

---

👉 Do you want me to now go **Encapsulation (Getters, Setters, Data Hiding with Constructors)** since it directly builds on Access Modifiers + `this` + Constructors?
