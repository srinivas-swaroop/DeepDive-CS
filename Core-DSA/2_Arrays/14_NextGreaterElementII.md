
---

# 🔹 Title

**L503 Next Greater Element II (Circular Array)**

---

# 🔹 Problem Statement

Given a **circular array** `nums`, return an array `res` where `res[i]` is the **next greater element** of `nums[i]`.

* The **next greater element** of `nums[i]` is the first element that appears (moving clockwise) which is **strictly greater** than `nums[i]`.
* If no greater element exists, `res[i] = -1`.

**Note:** Since the array is circular, after the last index, we continue checking from the beginning.

---

# 🔹 Examples

### Example 1

Input:

```
nums = [1, 2, 1]
```

Output:

```
[2, -1, 2]
```

Explanation:

* For `1` → next greater is `2`.
* For `2` → no greater element, so `-1`.
* For the last `1` → circularly, `2` is the next greater.

---

### Example 2 (Strictly Decreasing)

Input:

```
nums = [5, 4, 3, 2, 1]
```

Output:

```
[-1, 5, 5, 5, 5]
```

Explanation:

* For `5`, no greater element exists → `-1`.
* For `4`, next greater is `5`.
* Similarly, for `3`, `2`, and `1` → next greater is `5`.

---

### Example 3 (All Equal Elements)

Input:

```
nums = [2, 2, 2]
```

Output:

```
[-1, -1, -1]
```

Explanation:
No strictly greater element exists for any position.

---

# 🔹 Constraints

* `1 ≤ nums.length ≤ 10^4`
* `-10^9 ≤ nums[i] ≤ 10^9`

---

# 🔹 Hint

* **Brute force (O(n²))**: For each element, move forward until you find a greater number (or return `-1` if none exists).
* **Optimized (O(n))**: Use a **monotonic stack** and iterate twice to simulate circular behavior.

---

# 🔹 Pseudocode (Naive O(n²))

```
function nextGreaterElements(nums):
    n = length(nums)
    res = new array of size n

    for i in 0..n-1:
        idx = (i+1) % n
        count = 1
        found = false

        while count <= n:
            if nums[idx] > nums[i]:
                res[i] = nums[idx]
                found = true
                break
            idx = (idx+1) % n
            count++

        if not found:
            res[i] = -1

    return res
```

---

# 🔹 Java Code (Naive O(n²))

```java
class Solution {
    public int[] nextGreaterElements(int[] nums) {
        int n = nums.length;
        int[] arr = new int[n];

        for (int i = 0; i < n; i++) {
            int idx = (i + 1) % n;  // start checking from next element
            int count = 1;          // count steps taken
            boolean found = false;

            while (count <= n) {    // traverse at most n steps (full circle)
                if (nums[i] < nums[idx]) {
                    arr[i] = nums[idx];
                    found = true;
                    break;
                }
                idx = (idx + 1) % n;  // move circularly
                count++;
            }

            if (!found) {
                arr[i] = -1;   // no greater element found
            }
        }

        return arr;
    }
}
```

---

# 🔹 Complexity Analysis

* **Time Complexity:**

  * Outer loop runs `n` times.
  * Inner loop may run up to `n` times in the worst case.
  * Overall → **O(n²)**.
* **Space Complexity:**

  * Output array of size `n`.
  * No extra data structures used.
  * Overall → **O(1)** extra space.

---

# 🔹 Detailed Explanation of Code

1. **Loop through each element (`nums[i]`)**

   * For each number, we try to find its next greater element by moving forward.

2. **Check next elements circularly**

   * Start from `(i+1) % n` and keep moving.
   * Use `count` to ensure we don’t loop infinitely.
   * If we circle back to `i` without finding a greater element, assign `-1`.

3. **If greater element found → store it, else → `-1`**

👉 This is straightforward but slow for large `n` (10^4), which is why an **O(n) stack solution** is preferred in practice.

---

✅ This explanation matches your code exactly.
👉 Do you want me to now also include the **optimized (O(n)) version** with the same structured explanation (side by side for comparison)?
