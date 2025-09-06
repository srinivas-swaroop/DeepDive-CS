Perfect 💡 — **Strings in Java** is one of the most fundamental and slightly tricky topics for beginners because of **immutability**, **String Pool**, and multiple classes like `String`, `StringBuilder`, and `StringBuffer`.
I’ll give you a **very detailed explanation**, covering **concepts + methods + code examples**.

Save this as:

```
Java-Core/05_Strings.md
```

---

# 📘 Strings in Java

In Java, **strings are objects** that represent a sequence of characters.
Unlike primitive types, strings are **immutable objects** in Java.

---

## 1. String Basics

### 1.1 Creating Strings

1. Using **string literals** (stored in *String Pool* inside Heap):

```java
String s1 = "Hello";
```

2. Using **new keyword** (always creates a new object in Heap):

```java
String s2 = new String("Hello");
```

➡️ **Difference**:

* `s1 == s2` → `false` (different objects)
* `s1.equals(s2)` → `true` (same content)

---

### 1.2 Immutability of Strings

* Once created, **String objects cannot be modified**.
* Any modification creates a new String object.

```java
String s = "Hello";
s.concat(" World");  
System.out.println(s); // "Hello", not "Hello World"
```

👉 To modify strings efficiently, use `StringBuilder` or `StringBuffer`.

---

## 2. Common String Methods

| Method                          | Description                     | Example                                  |
| ------------------------------- | ------------------------------- | ---------------------------------------- |
| `length()`                      | Returns string length           | `"Java".length()` → 4                    |
| `charAt(int index)`             | Returns char at index           | `"Java".charAt(2)` → 'v'                 |
| `substring(int start)`          | Substring from start index      | `"Hello".substring(2)` → "llo"           |
| `substring(int start, int end)` | Substring between indices       | `"Hello".substring(1, 4)` → "ell"        |
| `equals(Object o)`              | Compares content                | `"abc".equals("abc")` → true             |
| `equalsIgnoreCase(String s)`    | Case-insensitive comparison     | `"JAVA".equalsIgnoreCase("java")` → true |
| `compareTo(String s)`           | Lexical comparison              | `"a".compareTo("b")` → -1                |
| `toUpperCase()`                 | Converts to uppercase           | `"java".toUpperCase()` → "JAVA"          |
| `toLowerCase()`                 | Converts to lowercase           | `"JAVA".toLowerCase()` → "java"          |
| `trim()`                        | Removes leading/trailing spaces | `"  hi  ".trim()` → "hi"                 |
| `replace(old, new)`             | Replace characters              | `"java".replace('a','o')` → "jovo"       |
| `contains(String s)`            | Checks if substring exists      | `"hello".contains("ell")` → true         |
| `startsWith(String s)`          | Checks prefix                   | `"hello".startsWith("he")` → true        |
| `endsWith(String s)`            | Checks suffix                   | `"hello".endsWith("lo")` → true          |
| `split(String regex)`           | Splits into array               | `"a,b,c".split(",")` → \["a","b","c"]    |
| `toCharArray()`                 | Converts to char\[]             | `"java".toCharArray()`                   |
| `isEmpty()`                     | Checks if empty                 | `"".isEmpty()` → true                    |

---

## 3. String Pool vs Heap

* **String literals** are stored in a **String Pool** (special memory in Heap).
* Saves memory by reusing strings.

```java
String s1 = "Java";
String s2 = "Java";
System.out.println(s1 == s2); // true (same pool object)

String s3 = new String("Java");
System.out.println(s1 == s3); // false (different heap object)
```

---

## 4. Mutable Strings

Since **String is immutable**, Java provides:

### 🔹 4.1 StringBuilder (Non-Thread Safe, Fast)

```java
StringBuilder sb = new StringBuilder("Hello");
sb.append(" World");
System.out.println(sb); // Hello World
```

✅ Methods of `StringBuilder`:

| Method                   | Example                 | Output                 |
| ------------------------ | ----------------------- | ---------------------- |
| `append()`               | `sb.append("Java")`     | adds text              |
| `insert(int, str)`       | `sb.insert(1,"oo")`     | "Hoollo"               |
| `replace(start,end,str)` | `sb.replace(0,5,"Hi")`  | replaces substring     |
| `delete(start,end)`      | `sb.delete(0,2)`        | deletes substring      |
| `reverse()`              | `sb.reverse()`          | reverses string        |
| `capacity()`             | Returns buffer capacity | default 16 chars       |
| `length()`               | Length of string        | `"Hello".length()` → 5 |

---

### 🔹 4.2 StringBuffer (Thread Safe, Synchronized)

Same as `StringBuilder`, but synchronized (safe in multithreaded environments, slower).

```java
StringBuffer sbf = new StringBuffer("Hello");
sbf.append(" Java");
System.out.println(sbf); // Hello Java
```

---

## 5. Example Programs

### 5.1 Palindrome Check

```java
public class Palindrome {
    public static void main(String[] args) {
        String str = "madam";
        StringBuilder sb = new StringBuilder(str);
        if (str.equals(sb.reverse().toString())) {
            System.out.println("Palindrome");
        } else {
            System.out.println("Not Palindrome");
        }
    }
}
```

---

### 5.2 Count Vowels and Consonants

```java
public class VowelCount {
    public static void main(String[] args) {
        String str = "Hello World";
        str = str.toLowerCase();
        int vowels = 0, consonants = 0;

        for (char c : str.toCharArray()) {
            if ("aeiou".indexOf(c) != -1) vowels++;
            else if (c >= 'a' && c <= 'z') consonants++;
        }

        System.out.println("Vowels: " + vowels);
        System.out.println("Consonants: " + consonants);
    }
}
```

---

### 5.3 Reverse Each Word

```java
public class ReverseWords {
    public static void main(String[] args) {
        String sentence = "Java is fun";
        String[] words = sentence.split(" ");

        StringBuilder result = new StringBuilder();
        for (String word : words) {
            result.append(new StringBuilder(word).reverse()).append(" ");
        }

        System.out.println(result.toString().trim());
        // Output: avaJ si nuf
    }
}
```

---

## 6. Choosing Between String, StringBuilder, StringBuffer

| Class           | Mutable? | Thread-Safe?    | Performance            | When to Use            |
| --------------- | -------- | --------------- | ---------------------- | ---------------------- |
| `String`        | No       | Yes (immutable) | Slow for modifications | When data won’t change |
| `StringBuilder` | Yes      | No              | Fast                   | Single-threaded apps   |
| `StringBuffer`  | Yes      | Yes             | Slower                 | Multi-threaded apps    |

---

## 7. Summary

* **String** → Immutable, stored in String Pool.
* **StringBuilder** → Mutable, fast, not thread-safe.
* **StringBuffer** → Mutable, thread-safe, slower.
* Use **methods** like `substring`, `replace`, `split`, `equals`, etc.
* Prefer `StringBuilder` when modifying strings frequently.

---

👉 Do you want me to also prepare a **big summary cheat sheet (1-page table)** of **all String, StringBuilder, and StringBuffer methods with examples** so learners can use it as a quick reference?
