Sure! Let’s create a **detailed Java guide for “Reverse Array”** with all the sections you requested. I’ll structure it professionally so it’s suitable for learning or documentation.

---

# **Reverse Array**

## **Problem Statement**

Given an array of integers, reverse the elements of the array **in place**. You should not use any additional arrays for reversing (i.e., the reversal must be done by modifying the original array).

**Function Signature:**

```java
void reverseArray(int[] arr)
```

---

## **Examples**

**Example 1:**
Input: `[1, 2, 3, 4, 5]`
Output: `[5, 4, 3, 2, 1]`

**Example 2:**
Input: `[10, 20, 30]`
Output: `[30, 20, 10]`

**Example 3 (Edge Case):**
Input: `[1]`
Output: `[1]`

**Example 4 (Edge Case):**
Input: `[]`
Output: `[]`

**Example 5 (Negative numbers & zero):**
Input: `[0, -1, -2, -3]`
Output: `[-3, -2, -1, 0]`

---

## **Constraints**

* The array size `n` satisfies `0 <= n <= 10^6`
* Array elements are integers: `-10^9 <= arr[i] <= 10^9`
* Must reverse **in place**. Extra memory usage should be O(1).

---

## **Hint**

* Use **two-pointer technique**:

  1. Start one pointer at the beginning and one at the end.
  2. Swap the elements at these pointers.
  3. Move the pointers toward each other until they meet or cross.

---

## **Pseudocode**

```
function reverseArray(arr):
    start = 0
    end = length of arr - 1

    while start < end:
        swap arr[start] with arr[end]
        start = start + 1
        end = end - 1

    return arr
```

---

## **Java Code**

```java
import java.util.Arrays;

public class ReverseArray {

    // Function to reverse the array in place
    public static void reverseArray(int[] arr) {
        int start = 0;
        int end = arr.length - 1;

        while (start < end) {
            // Swap arr[start] and arr[end]
            int temp = arr[start];
            arr[start] = arr[end];
            arr[end] = temp;

            // Move pointers
            start++;
            end--;
        }
    }

    public static void main(String[] args) {
        int[] arr1 = {1, 2, 3, 4, 5};
        reverseArray(arr1);
        System.out.println(Arrays.toString(arr1)); // Output: [5, 4, 3, 2, 1]

        int[] arr2 = {10, 20, 30};
        reverseArray(arr2);
        System.out.println(Arrays.toString(arr2)); // Output: [30, 20, 10]

        int[] arr3 = {}; // Edge case: empty array
        reverseArray(arr3);
        System.out.println(Arrays.toString(arr3)); // Output: []

        int[] arr4 = {0, -1, -2, -3}; // Negative numbers
        reverseArray(arr4);
        System.out.println(Arrays.toString(arr4)); // Output: [-3, -2, -1, 0]
    }
}
```

---

## **Complexity Analysis**

| Operation        | Complexity                                       |
| ---------------- | ------------------------------------------------ |
| Time Complexity  | O(n) – Each element is swapped once.             |
| Space Complexity | O(1) – In-place reversal, no extra array needed. |

* `n` is the length of the array.
* The solution efficiently handles large arrays due to O(n) time and constant space.

---

✅ This is a **complete learning-ready structure**: problem, examples, edge cases, constraints, hint, pseudocode, code, and complexity.

---

If you want, I can also make a **version that returns a new reversed array** and explain when that is preferred over in-place reversal. This is often useful in functional programming or immutable data situations.

Do you want me to include that too?
