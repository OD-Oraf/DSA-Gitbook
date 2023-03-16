# Lowest Common ancestor of binary search tree

## Strategy(DFS) Recursive approach

* 3 conditions. 1. if p and q both larger than parent, use root.right as ancestor. 2. If p and q are smaller than parent, use root.left as ancestor. 3. If p and q are mismatched, return root.

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */

class Solution {
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        
        /** 3 conditions to consier
         1. If p and q are less than root, set the left subtree root as the ancestor to check
         2. If p nad q are greater than root, set the right subtree root as ancestor to check
         3. If p and q are mismatched the, current root is the ancestor
        **/
        
        TreeNode ancestor = root;
        int pVal = p.val;
        int qVal = q.val;
        
        if (pVal < root.val && qVal < root.val) {
            return lowestCommonAncestor(root.left, p, q);
        } else if (pVal > root.val && qVal > root.val) {
            return lowestCommonAncestor(root.right, p, q);
        } else {
            return root;
        }
        
        
    }
}
```

## Iterative implementation

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */

class Solution {
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        // Check is p and q are on same side of tree iterativly
        
        if (root == null) {
            return root;
        }
        
        while (root != null) {
            if (p.val > root.val && q.val > root.val) {
                root = root.right;
            } else if (p.val < root.val && q.val < root.val) {
                root = root.left;
            } else {
                return root; // return the root where we find the split
            }
        }
        
        return root;
        
    }
}
```
