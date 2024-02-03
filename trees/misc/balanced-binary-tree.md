# Balanced Binary Tree

## Top Down Approach

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
    public boolean isBalanced(TreeNode root) {
        if (root == null) {
            return true;
        }
        
        return Math.abs(height(root.left) - height(root.right)) <= 1 
            && isBalanced(root.left)
            && isBalanced(root.right);
        
        
    }
    
    public int height(TreeNode root) {
        if (root == null) {
            return 0;
        }
        
        int leftHeight = height(root.left);
        int rightHeight = height(root.right);
        
        return 1 + Math.max(leftHeight, rightHeight);
    }
}
```

### Time/Space

Time O(nlogn) - Come back and understand

## Bottom UP Approach

```java
public class Solution {
    private boolean result = true;
    
    public boolean isBalanced(TreeNode root) {
        maxDepth(root);
        return result;
    }

    public int maxDepth(TreeNode root) {
        if (root == null)
            return 0;
        int l = maxDepth(root.left);
        int r = maxDepth(root.right);
        if (Math.abs(l - r) > 1) // dont want the difference to excceed 1 when left and right are returned
            result = false;
        return 1 + Math.max(l, r);
    }
}
```
