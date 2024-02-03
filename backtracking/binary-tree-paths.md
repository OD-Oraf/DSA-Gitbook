# Binary Tree Paths

## Strategy - Backtracking

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
    public List<String> binaryTreePaths(TreeNode root) {
        LinkedList<String> ans = new LinkedList();
        backtrack(root, new StringBuilder(), ans);
        return ans;
        
    }
    
    public void backtrack(TreeNode root, StringBuilder sb, LinkedList<String> ans) {
        if (root != null) {
            int length = sb.length();//length is used for backtrack by only including up to length
            sb.append(root.val);
            if (root.left == null && root.right == null) {//push leaf to path
                ans.add(sb.toString());
            } else {
                sb.append("->");
                backtrack(root.left, sb, ans);
                backtrack(root.right, sb, ans);
            }
            sb.setLength(length);
        }
    }
}
```
