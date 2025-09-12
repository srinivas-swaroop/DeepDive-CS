Sure! Let’s break this problem down thoroughly and clearly.

---

## **L171-Problem Statement**

You are given a string `columnTitle` representing an Excel column name. You need to return its corresponding **column number**.

Excel columns follow this pattern:

```
A -> 1
B -> 2
...
Z -> 26
AA -> 27
AB -> 28
...
ZY -> 701
...
```

The problem is essentially converting a **base-26 "alphabet" number system** to an integer.

---

## **Examples**

1. **Input:** `"A"`
   **Output:** `1`

2. **Input:** `"AB"`
   **Output:** `28`
   **Explanation:** A = 1, B = 2 → 1\*26 + 2 = 28

3. **Input:** `"ZY"`
   **Output:** `701`
   **Explanation:** Z = 26, Y = 25 → 26\*26 + 25 = 701

---

## **Constraints**

* `1 <= columnTitle.length <= 7`
* `columnTitle` consists only of uppercase English letters.
* `columnTitle` is in the range \["A", "FXSHRXW"].

---

## **Hint**

* Treat it like converting a **number from base-26** to decimal, where `'A' = 1, ..., 'Z' = 26`.
* Start from the **leftmost letter** (highest power of 26) and move to the rightmost (lowest power).

---

## **Pseudocode**

```
function titleToNumber(columnTitle):
    sum = 0
    power = length(columnTitle) - 1

    for each character ch in columnTitle:
        value = ch - 'A' + 1
        sum += value * (26^power)
        power -= 1

    return sum
```

---

## **Java Code**

```java
class Solution {
    public int titleToNumber(String columnTitle) {
        int len = columnTitle.length();
        int sum = 0;
        int power = len - 1;

        for (int i = 0; i < len; i++) {
            int letterValue = columnTitle.charAt(i) - 'A' + 1;
            sum += letterValue * (int)Math.pow(26, power);
            power--;
        }

        return sum;
    }
}
```

---

## **Time & Space Complexity**

* **Time Complexity:**
  `O(n)` where `n` is the length of the string (maximum 7).
  *Each character is processed once, `Math.pow` is O(1) here since max 26^6 is manageable.*

* **Space Complexity:**
  `O(1)` (no extra space proportional to input size).

