Got it 👍 You’re asking for **Control Statements in Java** (not Control Systems like in ECE 😅).
For a **Core Java learner’s repo**, this is the next big concept after Input/Output.
I’ll give you a **very detailed explanation** with all types of control statements, flowcharts, and examples.

You can save this as:

```
Java-Core/04_ControlStatements.md
```

---

# 📘 Control Statements in Java

Control statements determine the **flow of execution** of a program.
They allow us to make decisions, repeat actions, or skip code based on conditions.

In Java, control statements are divided into three main categories:

1. **Decision-Making Statements (Selection)**

   * `if`, `if-else`, `if-else-if ladder`, `switch`
2. **Looping Statements (Iteration)**

   * `for`, `while`, `do-while`, **enhanced for-each**
3. **Jump Statements (Branching)**

   * `break`, `continue`, `return`

---

## 1. Decision-Making Statements

### 🔹 1.1 `if` Statement

Executes a block only if condition is true.

```java
int age = 20;
if (age >= 18) {
    System.out.println("You are eligible to vote.");
}
```

---

### 🔹 1.2 `if-else` Statement

Provides an alternative if condition is false.

```java
int num = 5;
if (num % 2 == 0) {
    System.out.println("Even number");
} else {
    System.out.println("Odd number");
}
```

---

### 🔹 1.3 `if-else-if` Ladder

Used when multiple conditions need to be checked.

```java
int marks = 75;
if (marks >= 90) {
    System.out.println("Grade A+");
} else if (marks >= 75) {
    System.out.println("Grade A");
} else if (marks >= 50) {
    System.out.println("Grade B");
} else {
    System.out.println("Fail");
}
```

---

### 🔹 1.4 `switch` Statement

Selects one block of code from multiple options.
Introduced in Java 7, strings can also be used in `switch`.
Java 14+ added **switch expressions**.

```java
int day = 3;
switch (day) {
    case 1: System.out.println("Monday"); break;
    case 2: System.out.println("Tuesday"); break;
    case 3: System.out.println("Wednesday"); break;
    case 4: System.out.println("Thursday"); break;
    case 5: System.out.println("Friday"); break;
    case 6: System.out.println("Saturday"); break;
    case 7: System.out.println("Sunday"); break;
    default: System.out.println("Invalid day");
}
```

➡️ **Switch Expression (Java 14+)**

```java
int day = 3;
String result = switch (day) {
    case 1 -> "Monday";
    case 2 -> "Tuesday";
    case 3 -> "Wednesday";
    default -> "Invalid";
};
System.out.println(result); // Wednesday
```

---

## 2. Looping Statements

Loops are used for **repetition**.

### 🔹 2.1 `for` Loop

Used when the number of iterations is known.

```java
for (int i = 1; i <= 5; i++) {
    System.out.println("Count: " + i);
}
```

---

### 🔹 2.2 `while` Loop

Used when the number of iterations is unknown (condition checked first).

```java
int i = 1;
while (i <= 5) {
    System.out.println("Value: " + i);
    i++;
}
```

---

### 🔹 2.3 `do-while` Loop

Executes at least once (condition checked later).

```java
int i = 1;
do {
    System.out.println("Value: " + i);
    i++;
} while (i <= 5);
```

---

### 🔹 2.4 Enhanced `for-each` Loop

Used for arrays and collections.

```java
int[] numbers = {10, 20, 30, 40};
for (int num : numbers) {
    System.out.println(num);
}
```

---

## 3. Jump Statements

### 🔹 3.1 `break`

Exits from the nearest enclosing loop or switch.

```java
for (int i = 1; i <= 5; i++) {
    if (i == 3) break;
    System.out.println(i); // Prints 1, 2
}
```

---

### 🔹 3.2 `continue`

Skips the current iteration and continues with the next.

```java
for (int i = 1; i <= 5; i++) {
    if (i == 3) continue;
    System.out.println(i); // Skips 3
}
```

---

### 🔹 3.3 `return`

Used to exit from a method and optionally return a value.

```java
public static int sum(int a, int b) {
    return a + b;
}

public static void main(String[] args) {
    int result = sum(5, 7);
    System.out.println("Sum: " + result);
}
```

---

## 4. Example: Simple Calculator

```java
import java.util.Scanner;

public class Calculator {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter first number: ");
        double num1 = sc.nextDouble();

        System.out.print("Enter second number: ");
        double num2 = sc.nextDouble();

        System.out.print("Enter operator (+, -, *, /): ");
        char op = sc.next().charAt(0);

        double result;
        switch (op) {
            case '+': result = num1 + num2; break;
            case '-': result = num1 - num2; break;
            case '*': result = num1 * num2; break;
            case '/': result = (num2 != 0) ? num1 / num2 : Double.NaN; break;
            default: 
                System.out.println("Invalid operator");
                sc.close();
                return;
        }

        System.out.println("Result: " + result);
        sc.close();
    }
}
```

---

## 5. Summary

* **Decision-Making** → `if`, `if-else`, `switch`
* **Looping** → `for`, `while`, `do-while`, `for-each`
* **Jump** → `break`, `continue`, `return`

---

👉 Would you like me to also add **flowchart diagrams** (if-else, loops, switch) so that beginners can *visualize* the control flow?
