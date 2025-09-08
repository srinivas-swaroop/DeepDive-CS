Absolutely! Let’s create a **detailed guide for “Rotate Array” in Java** with all the sections you requested.

---

# **L189-Rotate Array**

## **Problem Statement**

Given an array of integers `arr` and an integer `k`, rotate the array to the **right by k steps**, where `k` is non-negative.

Rotation means each element moves to the right by `k` positions, and elements that fall off the end wrap around to the beginning.

**Function Signature:**

```java
void rotateArray(int[] arr, int k)
```

---

## **Examples**

**Example 1:**
Input: `arr = [1, 2, 3, 4, 5, 6, 7], k = 3`
Output: `[5, 6, 7, 1, 2, 3, 4]`

**Example 2:**
Input: `arr = [1, 2, 3], k = 4`
Output: `[3, 1, 2]`

> Note: `k` can be greater than array length. Use `k % arr.length` for effective rotation.

**Example 3 (Edge Case - Empty Array):**
Input: `arr = [], k = 2`
Output: `[]`

**Example 4 (Edge Case - k = 0):**
Input: `arr = [1, 2, 3], k = 0`
Output: `[1, 2, 3]`

**Example 5 (Edge Case - Single Element):**
Input: `arr = [10], k = 5`
Output: `[10]`

---

## **Constraints**

* `0 <= arr.length <= 10^6`
* `0 <= k <= 10^9`
* Array elements: `-10^9 <= arr[i] <= 10^9`
* Must rotate efficiently (avoid extra arrays if possible).

---

## **Hint**

1. **Optimal Approach Using Reversal Technique**:

   * Reverse the whole array.
   * Reverse the first `k` elements.
   * Reverse the remaining `n-k` elements.

2. **Two pointers or modulo arithmetic** helps to place elements at their new positions.

---

## **Pseudocode**

```
function rotateArray(arr, k):
    n = length of arr
    k = k % n  // effective rotation

    if n <= 1 or k == 0:
        return arr

    reverse(arr, 0, n-1)       // Reverse entire array
    reverse(arr, 0, k-1)       // Reverse first k elements
    reverse(arr, k, n-1)       // Reverse remaining elements

function reverse(arr, start, end):
    while start < end:
        swap arr[start] and arr[end]
        start = start + 1
        end = end - 1
```

---

## **Java Code**

```java
import java.util.Arrays;

public class RotateArray {

    // Function to rotate array to the right by k steps
    public static void rotateArray(int[] arr, int k) {
        int n = arr.length;
        if (n <= 1) return;       // No rotation needed
        k = k % n;                // Handle k > n

        reverse(arr, 0, n - 1);   // Reverse whole array
        reverse(arr, 0, k - 1);   // Reverse first k elements
        reverse(arr, k, n - 1);   // Reverse remaining n-k elements
    }

    // Helper function to reverse elements between start and end indices
    private static void reverse(int[] arr, int start, int end) {
        while (start < end) {
            int temp = arr[start];
            arr[start] = arr[end];
            arr[end] = temp;
            start++;
            end--;
        }
    }

    public static void main(String[] args) {
        int[] arr1 = {1, 2, 3, 4, 5, 6, 7};
        rotateArray(arr1, 3);
        System.out.println(Arrays.toString(arr1)); // [5, 6, 7, 1, 2, 3, 4]

        int[] arr2 = {1, 2, 3};
        rotateArray(arr2, 4);
        System.out.println(Arrays.toString(arr2)); // [3, 1, 2]

        int[] arr3 = {}; // Edge case: empty array
        rotateArray(arr3, 2);
        System.out.println(Arrays.toString(arr3)); // []

        int[] arr4 = {10}; // Edge case: single element
        rotateArray(arr4, 5);
        System.out.println(Arrays.toString(arr4)); // [10]
    }
}
```

---

## **Complexity Analysis**

| Operation        | Complexity                                            |
| ---------------- | ----------------------------------------------------- |
| Time Complexity  | O(n) – Each element is visited/swapped at most twice. |
| Space Complexity | O(1) – In-place rotation, no extra array used.        |

* `n` is the length of the array.
* Handles large `k` values efficiently using `k % n`.

---

This is a **complete, detailed guide** suitable for learning or documentation for Core Java developers.

---

If you want, I can also create a **“Rotate Array using extra array” approach** with simpler logic and explain **when each method is preferable**. It’s useful for beginners to understand both.

Do you want me to do that too?
