# Inorder Traversal (Recursive)

## Strategy

### _**Use helper function and pass in root and result**_

* Create helper function to build resulting ArrayList
* Recursively pass root node and result array into helper
  * Complete left tree, add node, complete right tree
    * helper(root.left, result)
    * result.add(root)
    * helper(root.right, result)

```java
 /* public class TreeNode {
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
    public List<Integer> inorderTraversal(TreeNode root) {
        List<Integer> result = new ArrayList<>();
        helper(root, result);
        return result;    
    }

    public static void helper(TreeNode root, List<Integer> result) {
        if (root != null) {
            helper(root.left, result);
            result.add(root.val);
            helper(root.right,result);
        }
    }     
}
```
