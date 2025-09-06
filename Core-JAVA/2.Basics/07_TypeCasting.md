Great pick 👌 — **Typecasting in Java** is another *must-know* concept for Java learners. Many developers get confused with **implicit/explicit casting**, **primitive casting**, and **object casting** (upcasting/downcasting).

I’ll give you a **very detailed explanation with examples, rules, pitfalls, and best practices**.

Save as:

```
Java-Core/07_TypeCasting.md
```

---

# 🎯 Typecasting in Java

**Typecasting** in Java means **converting one data type into another**.
It is of two main types:

1. **Primitive Casting** → between primitive types (`int`, `float`, etc.)
2. **Reference Casting** → between objects (parent ↔ child classes)

---

## 1. Primitive Typecasting

### 1.1 Widening (Implicit Casting / Type Promotion)

* Conversion from **smaller → larger** type.
* **Done automatically by Java** (no data loss).

Order:
`byte → short → int → long → float → double`

```java
public class WideningExample {
    public static void main(String[] args) {
        int a = 10;
        double d = a;  // int → double (automatic)
        System.out.println(d); // 10.0
    }
}
```

✔️ Safe conversion.
✔️ No data loss.

---

### 1.2 Narrowing (Explicit Casting / Type Demotion)

* Conversion from **larger → smaller** type.
* **Must be done manually** using `(type)` cast.
* May cause **data loss** or **overflow**.

```java
public class NarrowingExample {
    public static void main(String[] args) {
        double d = 9.78;
        int i = (int) d;  // double → int (manual cast)
        System.out.println(i); // 9 (decimal part lost)
    }
}
```

✔️ Possible data loss.
✔️ Explicit casting required.

---

### 1.3 Example of Overflow in Narrowing

```java
public class OverflowExample {
    public static void main(String[] args) {
        int a = 130;
        byte b = (byte) a;  // int → byte
        System.out.println(b); // -126 (overflow!)
    }
}
```

➡️ Why?

* `byte` range = -128 to 127.
* 130 goes out of range, so Java wraps around (modulo).

---

## 2. Typecasting with Characters

* `char` in Java is a **16-bit Unicode character**.
* Can be cast to/from `int`.

```java
public class CharCasting {
    public static void main(String[] args) {
        char c = 'A';
        int ascii = c;      // implicit widening
        System.out.println(ascii); // 65

        int num = 66;
        char ch = (char) num; // explicit narrowing
        System.out.println(ch); // 'B'
    }
}
```

---

## 3. Reference Typecasting (Objects)

For **classes** (non-primitive types), typecasting is about **inheritance hierarchy**.

### 3.1 Upcasting (Implicit Casting)

* Casting **child → parent class**.
* Done automatically.
* Safe, no explicit cast needed.

```java
class Animal {
    void sound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {
    void sound() {
        System.out.println("Bark");
    }
}

public class UpcastingExample {
    public static void main(String[] args) {
        Dog d = new Dog();
        Animal a = d;   // upcasting
        a.sound();      // Bark (runtime polymorphism)
    }
}
```

✔️ Useful in **polymorphism**.

---

### 3.2 Downcasting (Explicit Casting)

* Casting **parent → child class**.
* Must be done explicitly.
* Risky — may throw **`ClassCastException`** if not actually a child.

```java
class Animal {
    void sound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("Dog is barking");
    }
}

public class DowncastingExample {
    public static void main(String[] args) {
        Animal a = new Dog();   // upcasting
        Dog d = (Dog) a;        // downcasting (safe here)
        d.bark();               // Dog is barking
    }
}
```

⚠️ If object is not really a `Dog`, error occurs:

```java
Animal a = new Animal();
Dog d = (Dog) a;  // Runtime error: ClassCastException
```

---

## 4. The `instanceof` Operator

To avoid **ClassCastException** in downcasting, always check with `instanceof`.

```java
public class InstanceofExample {
    public static void main(String[] args) {
        Animal a = new Dog();

        if (a instanceof Dog) {
            Dog d = (Dog) a;
            d.bark();
        } else {
            System.out.println("Not a Dog!");
        }
    }
}
```

---

## 5. Real-World Analogy

* **Widening (upcasting)** → Putting a pen into a box (safe, fits).
* **Narrowing (downcasting)** → Taking a random thing from the box and assuming it’s a pen (unsafe unless checked).

---

## 6. Static vs Dynamic Casting

* **Primitive casting** → checked at **compile-time**.
* **Object casting** → checked at **runtime**.

---

## 7. Summary

| Casting Type          | Example        | Auto/Manual | Data Loss                    | Safe?               |
| --------------------- | -------------- | ----------- | ---------------------------- | ------------------- |
| Widening (Primitive)  | `int → double` | Auto        | No                           | ✅                   |
| Narrowing (Primitive) | `double → int` | Manual      | Yes (truncation/overflow)    | ⚠️                  |
| Upcasting (Object)    | `Dog → Animal` | Auto        | No                           | ✅                   |
| Downcasting (Object)  | `Animal → Dog` | Manual      | Risky (`ClassCastException`) | ⚠️ Use `instanceof` |

---

## 8. Quick Example (Mix of All Types)

```java
public class TypeCastingDemo {
    public static void main(String[] args) {
        // Primitive Casting
        int i = 100;
        double d = i;   // widening
        int j = (int) d; // narrowing

        // Char Casting
        char c = 'A';
        int ascii = c; // 65
        char ch = (char) 66; // 'B'

        // Object Casting
        Animal a = new Dog();  // upcasting
        if (a instanceof Dog) {
            Dog dog = (Dog) a;  // downcasting
            dog.bark();
        }
    }
}
```

---

✅ So, typecasting in Java is all about **safe conversions** between primitive types and objects, with rules to avoid **data loss** and **runtime exceptions**.

---

👉 Do you also want me to create a **diagram of memory + class hierarchy** (showing primitive casting flow and object upcasting/downcasting arrows)? That would make it super clear for learners.
