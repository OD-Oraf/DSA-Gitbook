# Maximum Depth of Binary Tree

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
    public int maxDepth(TreeNode root) {
        if (root == null) return 0;
	    Deque<TreeNode> dq = new ArrayDeque<>();
        int depth = 0;
        int levelSize = 0;
        TreeNode curr;
        
        dq.offer(root);
        
        while (!dq.isEmpty()) {
            depth++;
            levelSize = dq.size();
            for (int i = 0; i < levelSize; ++i) {
                curr = dq.poll();
                if (curr.left != null) dq.offer(curr.left);
                if (curr.right != null) dq.offer(curr.right);
            }
        }
        return depth;
    }
}
```
