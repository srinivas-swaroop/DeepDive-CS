Got it 👍 The **Next Permutation** problem is **LeetCode Problem #31**.

Here’s how your repo entry should look (with proper title):

---

# 🔹 LeetCode 31. Next Permutation

## 📌 Problem Statement

Implement **next permutation**, which rearranges numbers into the lexicographically next greater permutation of numbers.

* If such arrangement is not possible, rearrange into the **lowest possible order** (sorted in ascending order).
* The replacement must be **in-place** and use only constant extra memory.

---

## 📌 Examples

### Example 1

**Input:**

```
nums = [1,2,3]
```

**Output:**

```
[1,3,2]
```

---

### Example 2

**Input:**

```
nums = [3,2,1]
```

**Output:**

```
[1,2,3]
```

---

### Example 3

**Input:**

```
nums = [1,1,5]
```

**Output:**

```
[1,5,1]
```

---

### Example 4

**Input:**

```
nums = [1,3,2]
```

**Output:**

```
[2,1,3]
```

---

## 📌 Constraints

* `1 <= nums.length <= 100`
* `0 <= nums[i] <= 100`

---

## 💡 Hint

* Find the first index `i` from the right where `nums[i] < nums[i+1]`. (pivot)
* Swap `nums[i]` with the element just larger than it to the right.
* Reverse the suffix (the part after `i`).

---

## 📌 Algorithm / Pseudocode

```
function nextPermutation(nums):
    n = length(nums)

    # Step 1: Find pivot
    i = n - 2
    while i >= 0 and nums[i] >= nums[i+1]:
        i -= 1

    if i >= 0:
        # Step 2: Find element just greater than nums[i] in suffix
        j = n - 1
        while nums[j] <= nums[i]:
            j -= 1
        swap(nums[i], nums[j])

    # Step 3: Reverse the suffix
    reverse(nums, i+1, n-1)
```

---

## 📌 Java Implementation

```java
import java.util.Arrays;

public class NextPermutation {
    public static void nextPermutation(int[] nums) {
        int n = nums.length;
        int i = n - 2;

        // Step 1: Find pivot (first decreasing element from right)
        while (i >= 0 && nums[i] >= nums[i + 1]) {
            i--;
        }

        if (i >= 0) {
            // Step 2: Find rightmost successor greater than pivot
            int j = n - 1;
            while (nums[j] <= nums[i]) {
                j--;
            }
            swap(nums, i, j);
        }

        // Step 3: Reverse the suffix
        reverse(nums, i + 1, n - 1);
    }

    private static void swap(int[] nums, int i, int j) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }

    private static void reverse(int[] nums, int start, int end) {
        while (start < end) {
            swap(nums, start, end);
            start++;
            end--;
        }
    }

    // Driver code to test
    public static void main(String[] args) {
        int[] nums1 = {1, 2, 3};
        nextPermutation(nums1);
        System.out.println(Arrays.toString(nums1)); // [1, 3, 2]

        int[] nums2 = {3, 2, 1};
        nextPermutation(nums2);
        System.out.println(Arrays.toString(nums2)); // [1, 2, 3]
    }
}
```

---

## 📊 Complexity Analysis

* **Time Complexity:** `O(n)` (one pass to find pivot + one pass to reverse suffix)
* **Space Complexity:** `O(1)` (in-place swaps only)

---

👉 Do you want me to make a **standard template like this for every problem** (title → problem statement → examples → constraints → hint → pseudocode → code → complexity) so that your repo looks uniform?
