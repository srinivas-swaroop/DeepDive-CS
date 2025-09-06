Perfect 👌 — now we’re stepping into **Encapsulation + Packages** — two of the **biggest fundamentals** in Java for building clean, modular, and secure applications.
I’ll give you a **very detailed explanation** with **concepts, diagrams (text form), code, pros/cons, best practices**.

Save as:

```
Java-Core/12_Encapsulation_and_Packages.md
```

---

# 🛡️ Encapsulation & 📦 Packages in Java

---

## 1. Encapsulation in Java

### 🔹 Definition

Encapsulation = **Wrapping data (variables) + methods (functions) together into a single unit (class)** while **restricting direct access** to the data.

👉 It is often called **“Data Hiding”** in OOP.

---

### 🔹 Why Encapsulation?

* Protects data from unauthorized access.
* Controls how data is accessed or modified.
* Increases security and flexibility.
* Improves maintainability and readability.

---

### 🔹 How Encapsulation Works

✅ Declare class variables as **private**.
✅ Provide **public getter/setter methods** to access/modify them.

---

### 🔹 Example: Encapsulation

```java
class BankAccount {
    // Private variables → hidden from outside
    private String accountHolder;
    private double balance;

    // Constructor
    BankAccount(String name, double initialBalance) {
        this.accountHolder = name;
        this.balance = initialBalance;
    }

    // Public getter (read access)
    public String getAccountHolder() {
        return accountHolder;
    }

    // Public getter (read access)
    public double getBalance() {
        return balance;
    }

    // Public setter (controlled write access)
    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
            System.out.println("Deposited: " + amount);
        } else {
            System.out.println("Invalid deposit!");
        }
    }

    public void withdraw(double amount) {
        if (amount > 0 && balance >= amount) {
            balance -= amount;
            System.out.println("Withdrew: " + amount);
        } else {
            System.out.println("Invalid withdrawal or insufficient funds!");
        }
    }
}

public class Demo {
    public static void main(String[] args) {
        BankAccount acc = new BankAccount("Swaroop", 1000);

        // Access through public methods only
        System.out.println("Holder: " + acc.getAccountHolder());
        System.out.println("Balance: " + acc.getBalance());

        acc.deposit(500);
        acc.withdraw(200);
        System.out.println("Final Balance: " + acc.getBalance());
    }
}
```

✔️ Here `balance` is **private**, so direct manipulation like `acc.balance = -999;` is ❌ not possible.

---

### 🔹 Real-World Analogy

Encapsulation is like an **ATM Machine**:

* You don’t directly touch the **cash vault** (private data).
* You access it via **buttons on ATM** (public methods).
* ATM ensures rules: you can’t withdraw more than your balance.

---

### 🔹 Advantages of Encapsulation

* ✅ Security: sensitive data is protected.
* ✅ Flexibility: internal implementation can change without affecting external code.
* ✅ Reusability: encapsulated classes can be reused.
* ✅ Maintainability: easier to debug and extend.

---

---

## 2. Packages in Java

### 🔹 Definition

A **package** in Java is a **collection of classes, interfaces, and sub-packages** grouped together.
It provides **modularity, code organization, and namespace management**.

Think of packages as **folders in your file system**.

---

### 🔹 Why Use Packages?

* Avoids **naming conflicts**.
* Provides **modularity** (group related classes together).
* Easier to **maintain** large projects.
* Access control → package-private (`default`) access.

---

### 🔹 Types of Packages

1. **Built-in Packages** → already available in Java (e.g., `java.util`, `java.io`).
2. **User-defined Packages** → created by developers for custom projects.

---

### 🔹 Using Built-in Packages

```java
import java.util.Scanner;

public class Demo {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in); // from java.util package
        System.out.print("Enter your name: ");
        String name = sc.nextLine();
        System.out.println("Hello, " + name);
    }
}
```

✔️ Here `Scanner` belongs to `java.util` package.

---

### 🔹 Creating User-defined Packages

**Step 1: Create package**

```java
// File: mypackage/Calculator.java
package mypackage;

public class Calculator {
    public int add(int a, int b) {
        return a + b;
    }
}
```

**Step 2: Use package in another file**

```java
// File: Demo.java
import mypackage.Calculator;

public class Demo {
    public static void main(String[] args) {
        Calculator c = new Calculator();
        System.out.println("Sum: " + c.add(10, 20));
    }
}
```

**Step 3: Compile & Run**

```sh
javac -d . mypackage/Calculator.java Demo.java
java Demo
```

---

### 🔹 Sub-Packages

* Packages can have **nested sub-packages** (like folders inside folders).

Example:

```
com.company.project.module
```

```java
package com.company.project.module;

public class Test {
    public void show() {
        System.out.println("Inside sub-package class");
    }
}
```

---

### 🔹 Access Modifiers with Packages

* **default** → accessible only within same package.
* **public** → accessible from any package.
* **protected** → accessible in same package + subclasses.

---

### 🔹 Real-World Analogy

* **Encapsulation** = **ATM Machine** (data + methods together, hidden rules).
* **Packages** = **Folders in your computer** → group files logically.

---

## 3. Encapsulation + Packages Together

* Encapsulation = secure data inside a class.
* Packages = organize multiple classes securely.
* Together → create **scalable, modular, secure software systems**.

---

## 4. Best Practices

✅ Always **encapsulate data** → make fields private, provide getters/setters.
✅ Use **packages for logical grouping** of classes (e.g., `db`, `ui`, `services`).
✅ Follow **naming convention**:

* `com.companyname.projectname.module` (reverse domain style).
  ✅ Avoid **god classes** → split into smaller packages for maintainability.

---

# ✅ Summary

* **Encapsulation** = Wrapping data + methods, ensuring security (using `private` + getters/setters).
* **Packages** = Grouping related classes into modules for organization & namespace control.
* **Access Modifiers** + **Packages** work together for security + modular design.

---

👉 Next, do you want me to go into **Inheritance (with detailed examples, types, method overriding, and real-world use cases)** — since it’s the next OOP concept after Encapsulation?
