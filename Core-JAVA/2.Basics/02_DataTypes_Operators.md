Perfect 💡 — that’s the **next natural topic** after Java introduction. Let’s prepare **Data Types + Operators (with explanations + examples)** in a beginner-friendly but detailed way for **Core Java learners**.

You can save this as:

```
Java-Core/02_DataTypes_Operators.md
```

---

# 📘 Java Data Types and Operators

## 1. Data Types in Java

Java is a **statically typed language**, meaning you must declare the type of a variable before using it.
Data types are broadly divided into:

### 🔹 1.1 Primitive Data Types (8 total)

| Data Type   | Size (bits)  | Range                | Default Value | Example                  |
| ----------- | ------------ | -------------------- | ------------- | ------------------------ |
| **byte**    | 8            | -128 to 127          | 0             | `byte b = 100;`          |
| **short**   | 16           | -32,768 to 32,767    | 0             | `short s = 32000;`       |
| **int**     | 32           | -2^31 to 2^31-1      | 0             | `int x = 100000;`        |
| **long**    | 64           | -2^63 to 2^63-1      | 0L            | `long l = 10000000000L;` |
| **float**   | 32           | \~6–7 decimal digits | 0.0f          | `float f = 3.14f;`       |
| **double**  | 64           | \~15 decimal digits  | 0.0d          | `double d = 3.14159;`    |
| **char**    | 16 (Unicode) | 0 to 65,535          | '\u0000'      | `char c = 'A';`          |
| **boolean** | 1 (logical)  | true/false           | false         | `boolean flag = true;`   |

➡️ **Note:** Unlike C/C++, `char` in Java is **2 bytes** (Unicode) instead of 1 byte (ASCII).

---

### 🔹 1.2 Non-Primitive Data Types

* **Strings** (`String str = "Hello";`)
* **Arrays** (`int[] arr = {1,2,3};`)
* **Classes / Objects**
* **Interfaces**

---

## 2. Type Casting in Java

Two types:

1. **Implicit Casting (Widening)** → smaller → larger (automatic)

   ```java
   int x = 10;
   double y = x;  // int → double
   ```
2. **Explicit Casting (Narrowing)** → larger → smaller (manual)

   ```java
   double pi = 3.14;
   int n = (int) pi; // double → int (fraction lost)
   ```

---

## 3. Operators in Java

### 🔹 3.1 Arithmetic Operators

| Operator | Meaning             | Example                         |
| -------- | ------------------- | ------------------------------- |
| `+`      | Addition            | `10 + 5 → 15`                   |
| `-`      | Subtraction         | `10 - 5 → 5`                    |
| `*`      | Multiplication      | `10 * 5 → 50`                   |
| `/`      | Division            | `10 / 3 → 3` (integer division) |
| `%`      | Modulus (remainder) | `10 % 3 → 1`                    |

👉 **Important:**

* If **both operands are int**, result is int.
* For floating-point, result is precise.

```java
System.out.println(10 / 3);    // 3 (int division)
System.out.println(10 / 3.0);  // 3.333... (double division)
```

---

### 🔹 3.2 Relational (Comparison) Operators

| Operator | Example  | Result |
| -------- | -------- | ------ |
| `==`     | `5 == 5` | true   |
| `!=`     | `5 != 3` | true   |
| `>`      | `5 > 3`  | true   |
| `<`      | `5 < 3`  | false  |
| `>=`     | `5 >= 5` | true   |
| `<=`     | `3 <= 5` | true   |

---

### 🔹 3.3 Logical Operators

| Operator   | Example         | Result  |        |   |         |      |
| ---------- | --------------- | ------- | ------ | - | ------- | ---- |
| `&&` (AND) | `true && false` | false   |        |   |         |      |
| \`         |                 | \` (OR) | \`true |   | false\` | true |
| `!` (NOT)  | `!true`         | false   |        |   |         |      |

---

### 🔹 3.4 Assignment Operators

| Operator | Example  | Equivalent To |
| -------- | -------- | ------------- |
| `=`      | `x = 10` | assign        |
| `+=`     | `x += 5` | `x = x + 5`   |
| `-=`     | `x -= 3` | `x = x - 3`   |
| `*=`     | `x *= 2` | `x = x * 2`   |
| `/=`     | `x /= 4` | `x = x / 4`   |
| `%=`     | `x %= 2` | `x = x % 2`   |

---

### 🔹 3.5 Unary Operators

| Operator | Example       | Meaning            |
| -------- | ------------- | ------------------ |
| `+`      | `+a`          | Positive           |
| `-`      | `-a`          | Negative           |
| `++`     | `a++` / `++a` | Increment          |
| `--`     | `a--` / `--a` | Decrement          |
| `~`      | `~a`          | Bitwise complement |
| `!`      | `!a`          | Logical NOT        |

---

### 🔹 3.6 Bitwise Operators

| Operator | Example   | Explanation          |     |            |
| -------- | --------- | -------------------- | --- | ---------- |
| `&`      | `a & b`   | Bitwise AND          |     |            |
| \`       | \`        | \`a                  | b\` | Bitwise OR |
| `^`      | `a ^ b`   | Bitwise XOR          |     |            |
| `~`      | `~a`      | Bitwise NOT          |     |            |
| `<<`     | `a << 1`  | Left shift           |     |            |
| `>>`     | `a >> 1`  | Right shift          |     |            |
| `>>>`    | `a >>> 1` | Unsigned right shift |     |            |

---

## 4. Example Code: Data Types & Operators

```java
public class DataTypesOperators {
    public static void main(String[] args) {
        // Primitive types
        int a = 10, b = 3;
        double x = 10.0, y = 3.0;

        // Arithmetic
        System.out.println("Integer Division: " + (a / b)); // 3
        System.out.println("Floating Division: " + (x / y)); // 3.3333
        System.out.println("Remainder: " + (a % b)); // 1

        // Relational
        System.out.println("a > b: " + (a > b)); // true
        System.out.println("a == b: " + (a == b)); // false

        // Logical
        boolean cond1 = true, cond2 = false;
        System.out.println("cond1 && cond2: " + (cond1 && cond2)); // false
        System.out.println("cond1 || cond2: " + (cond1 || cond2)); // true

        // Assignment
        int num = 5;
        num += 2;  // num = 7
        System.out.println("num after += : " + num);

        // Bitwise
        int m = 5, n = 3; // 5=0101, 3=0011
        System.out.println("m & n: " + (m & n)); // 1 (0001)
        System.out.println("m | n: " + (m | n)); // 7 (0111)
        System.out.println("m ^ n: " + (m ^ n)); // 6 (0110)

        // Unary
        int val = 10;
        System.out.println("val++: " + (val++)); // 10
        System.out.println("++val: " + (++val)); // 12
    }
}
```

---

✅ This section now covers:

* Data types + memory sizes + ranges
* Type casting
* All operators (arithmetic → bitwise)
* Practical code examples

---

Would you like me to also add **practice questions + small coding exercises** (like “swap two numbers without a third variable”, “check odd/even using bitwise”) at the end of each topic so learners can practice?
