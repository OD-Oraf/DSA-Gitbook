# Balanced Binary Tree

Balanced tree: no more than 1 level of height difference between left and right sub trees

Each&#x20;





## Strategy(DFS)

* Use separate function to calculate height of longest path

## Difficult parts explained

Each sub tree should be treated as a subproblem

```java
return 1 + Math.max(height(root.left), height(root.right));
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
    public int height(TreeNode root) {
        if (root == null) {
            return -1; // null node doesnt count as level. subtract from height
        }
        
        return 1 + Math.max(height(root.left), height(root.right)); 
    }
    public boolean isBalanced(TreeNode root) {
        
        if (root == null) {
            return true;
        }
        int leftHeight = 0;
        int rightHeight = 0;
        
        leftHeight = height(root.left);
        rightHeight = height(root.right);
        
        if (Math.abs(leftHeight - rightHeight) <= 1 
            && isBalanced(root.left) 
            && isBalanced(root.right)) {
            return true;
        } 
        
        return false; 
    }
}
```
