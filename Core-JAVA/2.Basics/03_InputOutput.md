Great 👍 You’re building this like a **step-by-step Core Java guide**, so after **data types & operators**, the natural next step is **input/output in Java**.
I’ll give you a **beginner-friendly, detailed explanation** of `Scanner` and `System.out.print/println/printf`, with examples.

You can save this as:

```
Java-Core/03_InputOutput.md
```

---

# 📘 Input and Output in Java

## 1. Output in Java

In Java, output is mainly handled using the **`System.out` object**, which is an instance of `PrintStream`.

### 🔹 1.1 `print()`

* Prints text on the **same line**.
* Does **not** move the cursor to the next line.

```java
System.out.print("Hello ");
System.out.print("World!");
// Output: Hello World!
```

---

### 🔹 1.2 `println()`

* Prints text and **moves cursor to the next line**.
* Most commonly used.

```java
System.out.println("Hello");
System.out.println("World");
// Output:
// Hello
// World
```

---

### 🔹 1.3 `printf()`

* Used for **formatted output** (similar to C’s `printf`).
* Placeholders (format specifiers) are used.

| Format Specifier | Meaning        | Example                                       |
| ---------------- | -------------- | --------------------------------------------- |
| `%d`             | integer        | `System.out.printf("%d", 100);`               |
| `%f`             | floating-point | `System.out.printf("%.2f", 3.14159); // 3.14` |
| `%s`             | string         | `System.out.printf("Hi %s", "Swaroop");`      |
| `%c`             | character      | `System.out.printf("%c", 'A');`               |

```java
int age = 20;
double pi = 3.14159;
String name = "Swaroop";

System.out.printf("Name: %s, Age: %d, PI: %.2f%n", name, age, pi);
// Output: Name: Swaroop, Age: 20, PI: 3.14
```

👉 `%n` is the platform-independent newline (instead of `\n`).

---

## 2. Input in Java (Scanner Class)

To take input from the user, we use the **`Scanner` class** (introduced in Java 5).
It is part of the package:

```java
import java.util.Scanner;
```

Then create a scanner object:

```java
Scanner sc = new Scanner(System.in);
```

Here:

* `System.in` → standard input stream (keyboard).
* `Scanner` → reads and parses input.

---

### 🔹 2.1 Reading Different Data Types

| Method          | Description                           | Example                            |
| --------------- | ------------------------------------- | ---------------------------------- |
| `nextInt()`     | Reads an integer                      | `int n = sc.nextInt();`            |
| `nextDouble()`  | Reads a double                        | `double d = sc.nextDouble();`      |
| `nextFloat()`   | Reads a float                         | `float f = sc.nextFloat();`        |
| `nextLong()`    | Reads a long                          | `long l = sc.nextLong();`          |
| `next()`        | Reads a single word (till space)      | `String name = sc.next();`         |
| `nextLine()`    | Reads a whole line (including spaces) | `String line = sc.nextLine();`     |
| `nextBoolean()` | Reads true/false                      | `boolean flag = sc.nextBoolean();` |

---

### 🔹 2.2 Example: Reading Numbers

```java
import java.util.Scanner;

public class ScannerExample {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter an integer: ");
        int num = sc.nextInt();
        System.out.println("You entered: " + num);

        System.out.print("Enter a double: ");
        double d = sc.nextDouble();
        System.out.println("You entered: " + d);

        sc.close(); // Always close scanner
    }
}
```

---

### 🔹 2.3 Example: Reading Strings

```java
import java.util.Scanner;

public class ScannerStrings {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter your first name: ");
        String first = sc.next();  // stops at space

        sc.nextLine(); // consume leftover newline

        System.out.print("Enter your full name: ");
        String full = sc.nextLine(); // reads whole line

        System.out.println("First name: " + first);
        System.out.println("Full name: " + full);

        sc.close();
    }
}
```

⚠️ **Important Note**:
When using `next()` and then `nextLine()`, the `nextLine()` may capture just the leftover newline.
👉 Fix: use `sc.nextLine()` **after `next()`** to consume the newline.

---

### 🔹 2.4 Example: Mixed Inputs

```java
import java.util.Scanner;

public class MixedInput {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter your age: ");
        int age = sc.nextInt();

        sc.nextLine(); // consume leftover newline

        System.out.print("Enter your name: ");
        String name = sc.nextLine();

        System.out.printf("Hello %s, you are %d years old.%n", name, age);

        sc.close();
    }
}
```

---

## 3. Scanner vs Other Input Methods

* **BufferedReader** → Faster, but less user-friendly.
* **Scanner** → Easy to use, slower for competitive programming (parsing overhead).
* For **real-world apps** → Scanner is fine.
* For **CP/large input** → prefer `BufferedReader` or `FastIO`.

---

## 4. Common Mistakes with Scanner

1. **Forgetting `sc.close()`** → can cause resource leaks.
2. **Mixing `next()` and `nextLine()`** → handle newline properly.
3. **Using wrong method** → `nextInt()` vs `nextDouble()`.
4. **Input mismatch** → entering text when expecting numbers → `InputMismatchException`.

---

✅ Summary:

* Use **`System.out.print/println/printf`** for output.
* Use **`Scanner`** for input (`nextInt`, `nextLine`, etc.).
* Handle **newline issues** carefully.
* Always **close Scanner**.

---

👉 Do you want me to also include a **set of small practice problems** (like “sum of two numbers”, “simple calculator using scanner & operators”, “user details printing with formatting”) so learners can immediately try coding?
