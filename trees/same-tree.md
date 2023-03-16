# Same Tree

## Strategy(Check if values are the same recursively)

* Check if trees are null(same)
  * return true
* Check if one or other tree is null(different)
  * Return null&#x20;
* Check node values traversal
  *   return false if different



### Recursive Solution

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public boolean isSameTree(TreeNode p, TreeNode q) {
        if (p == null && q == null) {
            return true;
        }
        if (p == null || q == null) {
            return false;
        }
        if (p.val != q.val) {
            return false;
        }
        return  isSameTree(p.right, q.right) && isSameTree(p.left, q.left);
    }
}a
```
