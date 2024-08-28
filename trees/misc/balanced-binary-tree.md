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
    private boolean ans = true;
    public boolean isBalanced(TreeNode root) {
        if (root == null) {
            return ans;
        }
        checkBalance(root);
        return ans;
    }
    
    private int checkBalance(TreeNode root) {
        if (root == null) {
            return 0;
        }
        int leftPath = checkBalance(root.left);
        int rightPath = checkBalance(root.right);
        if (Math.abs(leftPath - rightPath) > 1) {
            ans = false;
        }
        
        return 1 + Math.max(leftPath, rightPath);
    }
}
```
