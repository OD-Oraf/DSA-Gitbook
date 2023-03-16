# Path Sum

## Strategy(DFS)

* Use DFS and at each node subtract node value from sum.&#x20;
* When you reach leafnode, check if it is equal to the sum

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
    public boolean hasPathSum(TreeNode root, int targetSum) {
        // End of path denoted by leaf node and node value is equal to sum
        
        if (root == null) {
            return false;
        }
        
        if (root.left == null && root.right == null && targetSum == root.val) {
            return true;
        }
        
        return hasPathSum(root.left, targetSum - root.val) || hasPathSum(root.right, targetSum - root.val);
        
    }
}
```
