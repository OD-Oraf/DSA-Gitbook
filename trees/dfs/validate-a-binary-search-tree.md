# Validate a Binary Search Tree

## Strategy - DFS

* All values on the left must strictly less than all the parent nodes
* All values on the right must be strictly greater than the parent nodes
* We can acheive this by updating valid boundaries at each node with the starting boundary for the root node being (-∞, ∞)
  * When we check left subtreee, update right boundary to parent node since no child nodes should exceed that value
  * When we check the right subtreee, update left boundary to the parent node since no child nodes should be less than that value

<figure><img src="../../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

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
    public boolean isValidBST(TreeNode root) {
        if (root == null) {
            return true;
        }
        return dfs(root, null, null);
        
    }
    
    public boolean dfs(TreeNode root, Integer min, Integer max) {
        if (root == null) {
            return true;
        }
        if (min != null && root.val <= min || max != null && root.val >= max) {
            return false;
        }
        
        return dfs(root.left, min, root.val) && dfs(root.right, root.val, max);
    }
}
```
