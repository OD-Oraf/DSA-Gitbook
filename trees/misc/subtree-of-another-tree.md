# Subtree of another tree

Link: [https://leetcode.com/problems/subtree-of-another-tree/](https://leetcode.com/problems/subtree-of-another-tree/)

## Strategy

This is just doing the same tree problem on each node

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
    public boolean isSubtree(TreeNode root, TreeNode subRoot) {
        if (root == null && subRoot == null) {
            return true;
        }
        if (root == null || subRoot == null) {
            return false;
        }
        
        if (isSameTree(root, subRoot) == true) {
            return true;
        }
        
        return isSubtree(root.left, subRoot) || isSubtree(root.right, subRoot);
        
        
        
    }
    public boolean isSameTree(TreeNode n1, TreeNode n2) {
         //basically isSame tree but checking each node
        if (n1 == null && n2 == null) {
            return true;
        }
        if (n1 == null || n2 == null) {
            return false;
        }
        
        if (n1.val != n2.val) {
            return false;
        }
        
        return isSameTree(n1.left, n2.left) 
            && isSameTree(n1.right, n2.right);
    }
}
```
