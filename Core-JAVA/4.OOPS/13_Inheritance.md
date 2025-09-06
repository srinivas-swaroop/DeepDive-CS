Perfect — now we are moving into **Inheritance**, one of the **most crucial OOP pillars** in Java. I’ll provide a **detailed explanation**, including **types of inheritance, rules, examples, method overriding, constructors, real-world analogy, and best practices** for core Java learners and developers.

Save this as:

```
Java-Core/13_Inheritance.md
```

---

# 🌳 Inheritance in Java (Detailed Explanation)

---

## 1. What is Inheritance?

* **Inheritance** is an OOP concept where **one class acquires the properties (fields) and behaviors (methods) of another class**.
* Helps in **code reusability**, **modularity**, and **polymorphism**.

**Terminology:**

* **Superclass / Parent class / Base class** → the class being inherited from.
* **Subclass / Child class / Derived class** → the class which inherits.

---

## 2. Syntax

```java
class Parent {
    // parent members
}

class Child extends Parent {
    // child members
}
```

---

## 3. Types of Inheritance in Java

1. **Single Inheritance** → One child inherits from one parent.
2. **Multilevel Inheritance** → Class A → B → C.
3. **Hierarchical Inheritance** → Multiple classes inherit from one parent.
4. **Hybrid Inheritance** → Combination of multilevel + hierarchical (achieved via interfaces in Java).

> ⚠️ Java **does not support multiple inheritance with classes** directly (Diamond problem) — use **interfaces** instead.

---

### 3.1 Single Inheritance Example

```java
class Animal {
    void eat() {
        System.out.println("Animal eats");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("Dog barks");
    }
}

public class Demo {
    public static void main(String[] args) {
        Dog d = new Dog();
        d.eat(); // inherited method
        d.bark(); // child method
    }
}
```

---

### 3.2 Multilevel Inheritance Example

```java
class Animal {
    void eat() { System.out.println("Animal eats"); }
}

class Mammal extends Animal {
    void walk() { System.out.println("Mammal walks"); }
}

class Dog extends Mammal {
    void bark() { System.out.println("Dog barks"); }
}

public class Demo {
    public static void main(String[] args) {
        Dog d = new Dog();
        d.eat();
        d.walk();
        d.bark();
    }
}
```

---

### 3.3 Hierarchical Inheritance Example

```java
class Animal {
    void eat() { System.out.println("Animal eats"); }
}

class Dog extends Animal {
    void bark() { System.out.println("Dog barks"); }
}

class Cat extends Animal {
    void meow() { System.out.println("Cat meows"); }
}
```

✔️ Both `Dog` and `Cat` inherit from `Animal`.

---

## 4. Method Overriding

* **Overriding** occurs when a **subclass provides its own implementation** of a **parent class method**.
* Rules:

  * Same method name, parameters, and return type.
  * Cannot reduce visibility (e.g., `protected` → `private` ❌).
  * Only instance methods can be overridden (static methods **cannot**).

```java
class Animal {
    void sound() { System.out.println("Animal sound"); }
}

class Dog extends Animal {
    @Override
    void sound() { System.out.println("Bark"); }
}

public class Demo {
    public static void main(String[] args) {
        Animal a = new Dog();
        a.sound(); // Bark → runtime polymorphism
    }
}
```

---

## 5. `super` Keyword

* Refers to **parent class members**.
* Used to:

  1. Access parent methods → `super.method()`
  2. Access parent constructor → `super()`

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

---

## 6. Rules of Inheritance in Java

1. Private members **cannot be inherited** (accessible via public/protected getters/setters).
2. Constructors are **not inherited**.
3. Static methods/fields belong to the class, **not inherited dynamically**.
4. Avoid multiple inheritance with classes → use interfaces instead.
5. `final` classes **cannot be inherited**.

---

## 7. Real-World Analogy

* **Parent class** = Vehicle (general blueprint).
* **Child class** = Car, Bike, Bus (specific versions).
* **Inherited behavior** = All vehicles can move.
* **Unique behavior** = Car honks, Bike pedals, Bus carries passengers.

---

## 8. Advantages of Inheritance

* ✅ Code Reusability → no need to rewrite parent logic.
* ✅ Extensibility → easy to add new features.
* ✅ Polymorphism → method overriding enables runtime flexibility.
* ✅ Logical Hierarchy → models real-world relationships.

---

## 9. Important Notes

* **Single Inheritance** → simple, easy to maintain.
* **Multilevel** → careful with deep hierarchies (constructor order).
* **Hierarchical** → good for multiple child classes from one parent.
* Use **interfaces** for multiple inheritance.
* Use **abstract classes** when you want partial implementation.

---

## 10. Example: Combined Inheritance + Polymorphism

```java
abstract class Animal {
    abstract void sound();
    void eat() { System.out.println("Animal eats"); }
}

class Dog extends Animal {
    void sound() { System.out.println("Dog barks"); }
}

class Cat extends Animal {
    void sound() { System.out.println("Cat meows"); }
}

public class Demo {
    public static void main(String[] args) {
        Animal a1 = new Dog();
        Animal a2 = new Cat();

        a1.eat();    // inherited
        a1.sound();  // overridden → Dog barks
        a2.eat();
        a2.sound();  // overridden → Cat meows
    }
}
```

---

## 11. Best Practices

✅ Prefer **inheritance only for “is-a” relationship**.
✅ Use **composition over inheritance** when possible.
✅ Avoid **deep hierarchies** → can make code hard to maintain.
✅ Always use **`@Override` annotation** for overridden methods.
✅ Use **abstract classes** if parent provides partial implementation.

---

# ✅ Summary

* **Inheritance** = one class inherits properties & methods of another.
* **Types**: Single, Multilevel, Hierarchical, Hybrid (via interfaces).
* **Method Overriding** → enables runtime polymorphism.
* **`super` keyword** → access parent members & constructors.
* **Rules** → private members not inherited, final classes cannot be inherited, static methods are class-level.

---

Next, we can go into **Polymorphism (Compile-time + Runtime) with detailed examples, overriding, overloading, and best practices** — which naturally follows inheritance.

Do you want me to continue with that?
