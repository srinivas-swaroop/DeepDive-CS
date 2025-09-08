Absolutely! Let’s create a **detailed guide for “Two Sum” in Java** with all sections you requested.

---

# **L1-Two Sum**

## **Problem Statement**

Given an array of integers `nums` and an integer `target`, return **indices of the two numbers** such that they add up to the `target`.

* You may assume that each input has **exactly one solution**.
* You may **not use the same element twice**.

**Function Signature:**

```java
int[] twoSum(int[] nums, int target)
```

---

## **Examples**

**Example 1:**
Input: `nums = [2, 7, 11, 15], target = 9`
Output: `[0, 1]`

> Explanation: `nums[0] + nums[1] = 2 + 7 = 9`

**Example 2:**
Input: `nums = [3, 2, 4], target = 6`
Output: `[1, 2]`

**Example 3 (Edge Case - Negative numbers):**
Input: `nums = [-1, -2, -3, -4, -5], target = -8`
Output: `[2, 4]`

> Explanation: `nums[2] + nums[4] = -3 + -5 = -8`

**Example 4 (Edge Case - Single pair array):**
Input: `nums = [1, 1], target = 2`
Output: `[0, 1]`

---

## **Constraints**

* `2 <= nums.length <= 10^5`
* `-10^9 <= nums[i] <= 10^9`
* `-10^9 <= target <= 10^9`
* Exactly **one solution** exists for each input.

---

## **Hint**

* Use a **HashMap** to store numbers as you iterate through the array.
* Check if `target - nums[i]` exists in the map.
* This avoids the O(n²) brute-force method.

---

## **Pseudocode**

```
function twoSum(nums, target):
    create empty map: numToIndex

    for i from 0 to length(nums)-1:
        complement = target - nums[i]
        if complement exists in numToIndex:
            return [numToIndex[complement], i]
        else:
            numToIndex[nums[i]] = i

    return [] // default return, should not reach
```

---

## **Java Code (Optimized using HashMap)**

```java
import java.util.Arrays;
import java.util.HashMap;

public class TwoSum {

    public static int[] twoSum(int[] nums, int target) {
        HashMap<Integer, Integer> numToIndex = new HashMap<>();

        for (int i = 0; i < nums.length; i++) {
            int complement = target - nums[i];

            if (numToIndex.containsKey(complement)) {
                return new int[]{numToIndex.get(complement), i};
            }

            numToIndex.put(nums[i], i);
        }

        // This should never happen as per problem statement
        return new int[]{};
    }

    public static void main(String[] args) {
        int[] nums1 = {2, 7, 11, 15};
        int target1 = 9;
        System.out.println(Arrays.toString(twoSum(nums1, target1))); // [0, 1]

        int[] nums2 = {3, 2, 4};
        int target2 = 6;
        System.out.println(Arrays.toString(twoSum(nums2, target2))); // [1, 2]

        int[] nums3 = {-1, -2, -3, -4, -5};
        int target3 = -8;
        System.out.println(Arrays.toString(twoSum(nums3, target3))); // [2, 4]

        int[] nums4 = {1, 1};
        int target4 = 2;
        System.out.println(Arrays.toString(twoSum(nums4, target4))); // [0, 1]
    }
}
```

---

## **Complexity Analysis**

| Operation        | Complexity                                                         |
| ---------------- | ------------------------------------------------------------------ |
| Time Complexity  | O(n) – We traverse the array once and lookups in HashMap are O(1). |
| Space Complexity | O(n) – HashMap stores up to n elements.                            |

* `n` = length of the array.
* Efficient for large arrays due to single-pass solution.

---

Yes! If you want a **Two Sum solution with O(1) extra space**, you can achieve it using the **two-pointer technique**, but with a **sorted array**.

Here’s the detailed explanation:

---

# **Two Sum with O(1) Space (Two-Pointer Approach)**

## **Important Note**

* This **requires sorting the array** first.
* After sorting, original indices are lost, so you need to **store original indices** before sorting if you need them.
* If indices are not required, this works directly with O(1) extra space.

---

## **Approach**

1. Sort the array.
2. Use two pointers:

   * `left = 0`
   * `right = n - 1`
3. While `left < right`:

   * If `nums[left] + nums[right] == target` → return the pair.
   * If sum < target → move `left` forward.
   * If sum > target → move `right` backward.

---

## **Pseudocode**

```
function twoSum(nums, target):
    sort nums
    left = 0
    right = length(nums) - 1

    while left < right:
        sum = nums[left] + nums[right]
        if sum == target:
            return [nums[left], nums[right]]  // or indices if tracked
        else if sum < target:
            left++
        else:
            right--
```

---

## **Java Code (O(1) Extra Space)**

```java
import java.util.Arrays;

public class TwoSumO1Space {

    public static int[] twoSum(int[] nums, int target) {
        // Copy of original array to preserve indices if needed
        int[] arr = Arrays.copyOf(nums, nums.length);
        Arrays.sort(arr);

        int left = 0;
        int right = arr.length - 1;

        while (left < right) {
            int sum = arr[left] + arr[right];
            if (sum == target) {
                return new int[]{arr[left], arr[right]}; // returns values
            } else if (sum < target) {
                left++;
            } else {
                right--;
            }
        }

        return new int[]{}; // No solution found
    }

    public static void main(String[] args) {
        int[] nums = {2, 7, 11, 15};
        int target = 9;
        System.out.println(Arrays.toString(twoSum(nums, target))); // [2, 7]

        int[] nums2 = {3, 2, 4};
        int target2 = 6;
        System.out.println(Arrays.toString(twoSum(nums2, target2))); // [2, 4]
    }
}
```

---

## **Complexity Analysis**

| Operation        | Complexity                                                     |
| ---------------- | -------------------------------------------------------------- |
| Time Complexity  | O(n log n) – Sorting dominates. Two-pointer traversal is O(n). |
| Space Complexity | O(1) – Only a few variables used (ignoring sorting in-place).  |

---

✅ **Summary:**

* **HashMap approach:** O(n) time, O(n) space
* **Two-pointer sorted approach:** O(n log n) time, O(1) space (values, not indices unless tracked)

---

If you want, I can make a **true O(1) space solution that also returns original indices** without extra arrays. It’s trickier but doable.

Do you want me to show that?



