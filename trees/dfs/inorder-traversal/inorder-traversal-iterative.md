# Inorder Traversal(Iterative)

## Strategy

* Inorder - print node on second visit
* Use stack to keep track of visited nodes
  * Push to stack
  * Continue down left tree
    * curr = curr.left
* When current node becomes null (reach end of tree path)
  * Pop from stack
  * add to result
  * set current to curr.right
* Stopping condition
  * When Stack is empty and curr is null

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
    public List<Integer> inorderTraversal(TreeNode root) {
        
        List<Integer> result = new ArrayList<>(); 
        Stack<TreeNode> stack = new Stack<>();
        TreeNode curr = root;
        
        while (!stack.isEmpty() || curr != null) {
            while (curr != null) { // null inidcates end of tree path
                stack.push(curr);
                curr = curr.left;
            }
            curr = stack.pop();
            result.add(curr.val);
            curr = curr.right;
        }
        
        return result;
    }
}
```
