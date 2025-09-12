Here’s a **complete breakdown** of LeetCode 152 – Maximum Product Subarray in the format you requested:

---

# **Title**

152. Maximum Product Subarray

---

# **Problem Statement**

Given an integer array `nums`, find a **contiguous subarray** (containing at least one number) which has the **largest product**, and return that product.

---

# **Examples**

**Example 1:**

```
Input: nums = [2,3,-2,4]
Output: 6
Explanation: Subarray [2,3] has the largest product 6.
```

**Example 2:**

```
Input: nums = [-2,0,-1]
Output: 0
Explanation: The result cannot be 2, because [-2,-1] is not contiguous with 0.
```

---

# **Edge Cases**

1. Single element array: `[5]` → output `5`
2. Single negative element: `[-5]` → output `-5`
3. All negatives, odd count: `[-1,-2,-3]` → max product by skipping one negative.
4. Zeros in between: `[2,3,0,-2,4]` → resets the product.
5. Large mix: `[1,0,-1,2,3,-5,-2]` → tricky flip due to negatives.

---

# **Constraints**

* `1 <= nums.length <= 2 * 10^4`
* `-10 <= nums[i] <= 10`
* The product of any subarray fits in a 32-bit integer.

---

# **Hint**

* Track **both maximum and minimum product** at each step because negative numbers can flip the sign.
* Consider scanning **both left-to-right and right-to-left** to handle zeros and negatives.

---

# **Pseudocode**

**Brute Force Approach (O(n²))**

```
maxProduct = -∞
for i = 0 to n-1:
    product = 1
    for j = i to n-1:
        product *= nums[j]
        maxProduct = max(maxProduct, product)
return maxProduct
```

**Optimal Approach (O(n))**

* Initialize `currMax = nums[0]`, `currMin = nums[0]`, `ans = nums[0]`
* For each element `nums[i]` (i ≥ 1):

  * temp = currMax
  * currMax = max(nums\[i], currMax*nums\[i], currMin*nums\[i])
  * currMin = min(nums\[i], temp*nums\[i], currMin*nums\[i])
  * ans = max(ans, currMax)
* Return `ans`

Alternative **Prefix-Suffix Scan**:

* Track running product from left (`pre`) and right (`suf`) simultaneously.
* Reset to 1 when hitting zero.
* Update global max at each step: `max = max(max, pre, suf)`

---

# **Code**

### **Brute Force (O(n²))**

```java
class Solution {
    public int maxProduct(int[] nums) {
        int n = nums.length;
        if (n == 1) return nums[0];
        
        int globalMax = Integer.MIN_VALUE;

        for (int j = 0; j < n; j++) {
            int localMax = nums[j];
            globalMax = Math.max(globalMax, localMax);  

            for (int k = j + 1; k < n; k++) {
                localMax *= nums[k];
                globalMax = Math.max(globalMax, localMax);
            }
        }
        return globalMax;
    }
}
```

### **Optimal DP (O(n))**

```java
class Solution {
    public int maxProduct(int[] nums) {
        int n = nums.length;
        int currMax = nums[0];
        int currMin = nums[0];
        int ans = nums[0];

        for (int i = 1; i < n; i++) {
            int temp = currMax;
            currMax = Math.max(nums[i], Math.max(currMax * nums[i], currMin * nums[i]));
            currMin = Math.min(nums[i], Math.min(temp * nums[i], currMin * nums[i]));
            ans = Math.max(ans, currMax);
        }
        return ans;
    }
}
```

### **Alternative Prefix–Suffix Scan (O(n))**

```java
class Solution {
    public int maxProduct(int[] nums) {
        int pre = 1, suf = 1;
        int max = Integer.MIN_VALUE;
        int n = nums.length;

        for(int i = 0; i < n; i++){
            pre = (pre == 0 ? 1 : pre) * nums[i];
            suf = (suf == 0 ? 1 : suf) * nums[n - 1 - i];
            max = Math.max(max, Math.max(pre, suf));
        }
        return max;
    }
}
```

---

# **Complexity Analysis**

| Approach               | Time Complexity | Space Complexity |
| ---------------------- | --------------- | ---------------- |
| Brute Force            | O(n²)           | O(1)             |
| DP (`currMax/currMin`) | O(n)            | O(1)             |
| Prefix–Suffix Scan     | O(n)            | O(1)             |

---

# **Common Mistakes**

1. Only tracking `currMax` → fails on negative numbers.
2. Resetting products incorrectly when hitting zero.
3. Forgetting that a **single negative element** can be the max if all else is smaller.
4. Confusing **subarray** vs **subsequence** — must be contiguous.
5. Trying to use sorting or sum-based tricks — wrong approach for product.

---


