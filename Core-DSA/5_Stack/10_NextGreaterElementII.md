Great 👍 Let’s now do the **Optimized O(n) solution** with the same structured format you like:

---

# 🔹 Title

**L507 Next Greater Element II (Circular Array) – Optimized Solution**

---

# 🔹 Problem Statement

You are given a **circular array** `nums`. For each element `nums[i]`, find the **next greater element**.

* The **next greater element** is the first element that appears clockwise which is **strictly greater** than `nums[i]`.
* If no such element exists, return `-1` for that index.

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

---

### Example 3 (All Equal)

Input:

```
nums = [2, 2, 2]
```

Output:

```
[-1, -1, -1]
```

---

# 🔹 Constraints

* `1 ≤ nums.length ≤ 10^4`
* `-10^9 ≤ nums[i] ≤ 10^9`

---

# 🔹 Hint

* Instead of checking every element (O(n²)), use a **monotonic decreasing stack**.
* Traverse the array **twice (2n)** to simulate circularity.
* When current number > stack’s top element, we found the "next greater" for that index.

---

# 🔹 Pseudocode (Optimized O(n))

```
function nextGreaterElements(nums):
    n = length(nums)
    result = array of size n filled with -1
    stack = empty stack (store indices)

    for i in 0..(2n-1):
        num = nums[i % n]
        while stack not empty and nums[stack.top] < num:
            result[stack.pop()] = num
        if i < n:
            stack.push(i)

    return result
```

---

# 🔹 Java Code (Optimized O(n))

```java
class Solution {
    public int[] nextGreaterElements(int[] nums) {
        int n = nums.length;
        int[] res = new int[n];
        Arrays.fill(res, -1); // default: -1
        Stack<Integer> stack = new Stack<>(); // store indices

        // Traverse array twice to simulate circular array
        for (int i = 0; i < 2 * n; i++) {
            int num = nums[i % n];
            
            // If current num is greater than stack's top → update result
            while (!stack.isEmpty() && nums[stack.peek()] < num) {
                res[stack.pop()] = num;
            }

            // Only push indices from first pass
            if (i < n) {
                stack.push(i);
            }
        }
        return res;
    }
}
```

---

# 🔹 Complexity Analysis

* **Time Complexity:**

  * Each index pushed and popped at most once → **O(n)**.
* **Space Complexity:**

  * Stack stores at most `n` indices → **O(n)**.

---

# 🔹 Detailed Explanation of Code

1. **Initialize result array with `-1`**

   * If no next greater exists, answer stays `-1`.

2. **Traverse array twice (`2n` times)**

   * To handle circular nature.
   * Index used is `i % n`.

3. **Monotonic stack (decreasing order)**

   * While the current element is greater than the element at the stack’s top index →
     update that index in result with current number.

4. **Push only first-pass indices**

   * So that every element has a chance to find its next greater.

---

✅ This solution is **much faster than O(n²)** and works well for `n = 10^4`.

---

👉 Do you want me to **present both solutions (Naive + Optimized) side-by-side in one final neatly tabular format** for easy revision (like for interviews/exams)?
