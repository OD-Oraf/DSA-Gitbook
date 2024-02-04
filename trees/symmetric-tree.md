# Symmetric Tree

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
    
    public boolean isSymmetric(TreeNode root) {
        
        return isMirror(root, root);
      
    }
    
    public static boolean isMirror (TreeNode root1, TreeNode root2) {
        if (root1 == null && root2 == null) {
            return true;
        }
        if (root1 == null || root2 == null) {
            return false;
        }
        
        return (root1.val == root2.val)
            && isMirror(root1.left, root2.right)
            && isMirror(root1.right, root2.left);
    } 
}
```

### ## Strategy - Recursive (bit more intuitive, less efficient)

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
    public boolean isSymmetric(TreeNode root) {
        
        if (root == null) {
            return true;
        }
        
        return symmetric(root.left, root.right);
        
    }
    
    public boolean symmetric(TreeNode leftSubtree, TreeNode rightSubtree) {
        if (leftSubtree == null && rightSubtree == null) { // Null subrees are symmetric
            return true;
        } else if (leftSubtree == null || rightSubtree == null) {
            return false;
        }
        
        
        if (leftSubtree.val != rightSubtree.val) {
            return false;
        } else {
            
            symmetric(leftSubtree.right, rightSubtree.left);
            return (leftSubtree.val == rightSubtree.val) // this is the main condition to be returned
                && symmetric(leftSubtree.left, rightSubtree.right) 
                && symmetric(leftSubtree.right, rightSubtree.left);
        }
    }
}
```

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
    public boolean isSymmetric(TreeNode root) {
        
        // Iterative solution using queue
        Queue<TreeNode> queue = new LinkedList<>();
        queue.add(root);
        queue.add(root); 
        while (!queue.isEmpty()) {
            TreeNode t1 = queue.poll(); // Take parent 1
            TreeNode t2 = queue.poll(); // Take parent 2 
            if (t1 == null && t2 == null) {
                continue;
            }
            if (t1 == null || t2 == null) {
                return false;
            }
            if (t1.val != t2.val) {
                return false;
            }
            
            queue.add(t1.left); // Two nodes are evaluated at once,
            queue.add(t2.right); // Compare left and right as part of symmetry
            queue.add(t1.right);
            queue.add(t2.left);
        }
        
        return true;
        
    }
}
```
