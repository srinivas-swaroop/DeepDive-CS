Got it 👍 You’re asking about **LeetCode 257 – Binary Tree Paths** and want the explanation in a structured format:

---

# **Binary Tree Paths (LeetCode 257)**

## **Problem Statement**

Given the `root` of a binary tree, return **all root-to-leaf paths** in the tree.
Each path should be represented as a string, with node values separated by `"->"`.

* A **leaf** is a node with no children.

---

## **Examples**

### Example 1:

**Input:**

```
    1
   / \
  2   3
   \
    5
```

**Output:**

```
["1->2->5","1->3"]
```

---

### Example 2:

**Input:**

```
  1
```

**Output:**

```
["1"]
```

---

### Example 3 (Edge Case – Skewed tree):

**Input:**

```
   1
    \
     2
      \
       3
```

**Output:**

```
["1->2->3"]
```

---

## **Constraints**

* Number of nodes: `1 ≤ n ≤ 100`
* Node values: `-100 ≤ Node.val ≤ 100`

---

## **Hint**

* Perform a **DFS (Depth First Search)** traversal.
* Maintain the current path as you go deeper.
* When you reach a **leaf node**, add the path string to the result list.
* Use `StringBuilder` or string concatenation (`path + "->" + node.val`) carefully to avoid mutating paths across recursive calls.

---

## **Pseudocode**

```
function binaryTreePaths(root):
    result = []
    if root is null:
        return result

    function dfs(node, path):
        if node is a leaf:
            add path to result
            return

        if node.left:
            dfs(node.left, path + "->" + node.left.val)
        if node.right:
            dfs(node.right, path + "->" + node.right.val)

    dfs(root, str(root.val))
    return result
```

---

## **Java Code**

```java
class Solution {
    List<String> list = new ArrayList<>();

    public List<String> binaryTreePaths(TreeNode root) {
        if (root == null) return list;
        dfs(root, new StringBuilder().append(root.val));
        return list;
    }

    private void dfs(TreeNode root, StringBuilder path) {
        // If leaf node → add to result
        if (root.left == null && root.right == null) {
            list.add(path.toString());
            return;
        }

        // Explore left subtree
        if (root.left != null) {
            StringBuilder leftPath = new StringBuilder(path);
            leftPath.append("->").append(root.left.val);
            dfs(root.left, leftPath);
        }

        // Explore right subtree
        if (root.right != null) {
            StringBuilder rightPath = new StringBuilder(path);
            rightPath.append("->").append(root.right.val);
            dfs(root.right, rightPath);
        }
    }
}
```

---

## **Complexity Analysis**

* **Time Complexity:** `O(n^2)`

  * Each node is visited once (`O(n)`),
  * But constructing a path string at each step costs up to `O(n)` in worst case.
  * Total → `O(n^2)`.

* **Space Complexity:**

  * `O(h)` for recursion stack (where `h` = height of tree, worst `O(n)` in skewed tree).
  * Output list stores all paths (could be up to `O(n)` strings, each of length `O(n)`).

---

👉 Do you also want me to show the **BFS (iterative) solution** for comparison, or just keep DFS?
