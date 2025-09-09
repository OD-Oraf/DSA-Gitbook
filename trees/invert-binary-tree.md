# Invert Binary Tree

### Strategy - Recursive DFS

* Switch left and right sub-trees
* Pass in left and right nodes to recursively switch the left and right sub-trees

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
    public TreeNode invertTree(TreeNode root) {
        
        // Via dfs - at each subtree we do the inversion
        if (root == null) {
            return null; // return null because we don't need this anser for our subproblems
        }
        
        TreeNode temp = root.left;
        root.left = root.right;
        root.right = temp;
        
        invertTree(root.left);
        invertTree(root.right);
        
        return root;
        
    }
}
```
````
Explanation

root = [2,1,3]       
     2
    / \
   1   3
   
invertTree(2);
root = 2,temp = 1 root.left = 3, root.right = 1 <- swap right and left
invertTree(root.left) -> invertTree(3)
invertTree(root.right) -> invertTree(1)
   
   invertTree(3)
   root = 3, temp = null, root.left = null, root.right = null
   invertTree(null) -> returns null;
   
   invertTree(1)
   root = 1, temp = null, root.left = null, root.right = null
   invertTree(null) -> return null;
   
   
return root
   

```

### Strategy - Iterative using deque

```javascript
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
    public TreeNode invertTree(TreeNode root) {
        
        // Iterative solution using dequue
        
        if (root == null) {
            return null; // not need for subproblems
        }
        
        Deque<TreeNode> stack = new LinkedList<>();
        stack.push(root);
        
        while (!stack.isEmpty()) {
            TreeNode node = stack.pop(); // current parent of subtree
            TreeNode temp = node.left; // temp for swap
            node.left = node.right; // swap 
            node.right = temp;
            
            if (node.left != null) {
                stack.push(node.left); // push left child if existing
            }
            if (node.right != null) {
                stack.push(node.right); // push right child if existing
            }
        }
        return root;
    }
}
```

### Strategy - BFS
