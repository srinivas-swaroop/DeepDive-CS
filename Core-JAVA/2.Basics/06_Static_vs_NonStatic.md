Got it 👍 — **Static vs Non-Static** is one of the most **core concepts** in Java, and it often confuses beginners.
I’ll break it down step by step with **concepts + differences + examples + best practices**.

Save this file as:

```
Java-Core/06_Static_vs_NonStatic.md
```

---

# ⚡ Static vs Non-Static in Java

In Java, everything belongs either to **the class (static)** or **the object (non-static)**.
Understanding this difference is crucial to mastering Java.

---

## 1. Static in Java

The keyword **`static`** means:

* The member **belongs to the class, not to an object**.
* Only **one copy** exists, shared among all objects.

### Static can be applied to:

* Variables (class variables)
* Methods
* Blocks
* Nested classes

---

### 1.1 Static Variables (Class Variables)

* Declared with `static` keyword inside a class.
* Shared by **all objects of the class**.

```java
class Student {
    String name;
    static String college = "VIT";  // static variable
    
    Student(String name) {
        this.name = name;
    }
    
    void display() {
        System.out.println(name + " - " + college);
    }
}

public class Demo {
    public static void main(String[] args) {
        Student s1 = new Student("Swaroop");
        Student s2 = new Student("Rahul");
        
        s1.display();  // Swaroop - VIT
        s2.display();  // Rahul - VIT
        
        // Changing static variable
        Student.college = "IIT";
        
        s1.display();  // Swaroop - IIT
        s2.display();  // Rahul - IIT
    }
}
```

👉 `college` belongs to the **class**, not individual students.

---

### 1.2 Static Methods

* Can be called **without creating an object**.
* Cannot access **non-static variables/methods directly**.
* Often used for **utility/helper functions**.

```java
class MathUtils {
    static int square(int x) {
        return x * x;
    }
}

public class Demo {
    public static void main(String[] args) {
        System.out.println(MathUtils.square(5)); // 25
    }
}
```

---

### 1.3 Static Block

* Runs only **once when the class is loaded** into JVM.
* Used for **initialization of static variables**.

```java
class Test {
    static int a;
    static {
        a = 10;
        System.out.println("Static block executed");
    }
}

public class Demo {
    public static void main(String[] args) {
        System.out.println(Test.a);  // triggers static block
    }
}
```

---

### 1.4 Static Nested Classes

* A class defined inside another class as `static`.
* Can be used without creating an object of the outer class.

```java
class Outer {
    static class Inner {
        void show() {
            System.out.println("Static nested class");
        }
    }
}

public class Demo {
    public static void main(String[] args) {
        Outer.Inner obj = new Outer.Inner();
        obj.show();
    }
}
```

---

## 2. Non-Static in Java (Instance Members)

* Belong to **objects**, not the class.
* Each object has its **own copy**.

```java
class Car {
    String color;   // non-static
    int speed;      // non-static
    
    Car(String color, int speed) {
        this.color = color;
        this.speed = speed;
    }
    
    void display() {
        System.out.println(color + " car runs at " + speed + " km/h");
    }
}

public class Demo {
    public static void main(String[] args) {
        Car c1 = new Car("Red", 100);
        Car c2 = new Car("Blue", 120);
        
        c1.display(); // Red car runs at 100 km/h
        c2.display(); // Blue car runs at 120 km/h
    }
}
```

👉 Each `Car` object has its **own color and speed**.

---

## 3. Static vs Non-Static — Key Differences

| Feature    | Static                       | Non-Static                     |
| ---------- | ---------------------------- | ------------------------------ |
| Belongs to | Class                        | Object                         |
| Memory     | Single copy shared           | Separate copy per object       |
| Access     | ClassName.member             | Object.member                  |
| Can access | Only static members directly | Both static and non-static     |
| Lifecycle  | Created when class loads     | Created when object is created |
| Example    | `Math.sqrt()`                | `car.speed`                    |

---

## 4. Example: Static vs Non-Static Together

```java
class Counter {
    static int count = 0;   // shared across objects
    int id;                 // unique for each object
    
    Counter() {
        count++;
        id = count;
    }
    
    void display() {
        System.out.println("Object ID: " + id + " | Total Objects: " + count);
    }
}

public class Demo {
    public static void main(String[] args) {
        Counter c1 = new Counter();
        Counter c2 = new Counter();
        Counter c3 = new Counter();
        
        c1.display();
        c2.display();
        c3.display();
    }
}
```

**Output:**

```
Object ID: 1 | Total Objects: 3
Object ID: 2 | Total Objects: 3
Object ID: 3 | Total Objects: 3
```

---

## 5. Best Practices

✅ Use **static** for:

* Constants (`final static`)
* Utility methods (`Math.sqrt()`)
* Shared properties (`college`, `count`)

❌ Don’t overuse static — it makes code **less object-oriented**.
❌ Avoid using **static variables for mutable data** (can cause bugs in multi-threading).

---

## 6. Real-World Example

```java
class BankAccount {
    static double interestRate = 5.0; // same for all accounts
    String accountHolder;
    double balance;
    
    BankAccount(String name, double balance) {
        this.accountHolder = name;
        this.balance = balance;
    }
    
    void display() {
        System.out.println(accountHolder + " | Balance: " + balance + " | Interest: " + interestRate + "%");
    }
}

public class Demo {
    public static void main(String[] args) {
        BankAccount a1 = new BankAccount("Swaroop", 5000);
        BankAccount a2 = new BankAccount("Rahul", 7000);
        
        a1.display();
        a2.display();
        
        // Update interest rate for all
        BankAccount.interestRate = 6.5;
        
        a1.display();
        a2.display();
    }
}
```

---

# ✅ Summary

* **Static** = belongs to the **class** (shared).
* **Non-static** = belongs to the **object** (unique per object).
* Use static for **constants, utilities, shared data**.
* Use non-static for **object-specific properties**.

---

👉 Do you also want me to prepare a **visual diagram (class memory layout: Heap vs Method Area)** showing where **static vs non-static variables live in memory**? That will give crystal clarity 🔥.
