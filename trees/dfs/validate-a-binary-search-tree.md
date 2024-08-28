# Validate a Binary Search Tree

## Strategy - DFS

* All values on the left must strictly less than all the parent nodes
* All values on the right must be strictly greater than the parent nodes
* We can acheive this by updating valid boundaries at each node with the starting boundary for the root node being (-∞, ∞)
  * When we check left subtreee, update right boundary to parent node since no child nodes should exceed that value
  * When we check the right subtreee, update left boundary to the parent node since no child nodes should be less than that value

<figure><img src="../../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

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
    public boolean isValidBST(TreeNode root) {
        /* 
        At each node we traverse, we need to be aware of the valid boundaries as the left tree              should not contain any values greater than all parents and the right subtree should             not contain any values less all parents
        */
        
        if (root == null) {
            return true;
        }
        return dfs(root, null, null); 
    }
    
    public boolean dfs(TreeNode root, Integer min, Integer max) {
        if (root == null) {
            return true;
        }
        
        if (min != null && root.val <= min || max != null && root.val >= max) {//make sure child nodes dont go out f valid boundaries
            return false;
        }
        
        return dfs(root.left, min, root.val) && dfs(root.right, root.val, max); 
    }
    
    
    
}
```

## Strategy - BST(Worse than DFS in this case)

```java
class Solution {
    private Deque<TreeNode> stack = new LinkedList();
    private Deque<Integer> upperLimits = new LinkedList();
    private Deque<Integer> lowerLimits = new LinkedList();

    public void update(TreeNode root, Integer low, Integer high) {
        stack.add(root);
        lowerLimits.add(low);
        upperLimits.add(high);
    }

    public boolean isValidBST(TreeNode root) {
        Integer low = null, high = null, val;
        update(root, low, high);

        while (!stack.isEmpty()) {
            root = stack.poll();
            low = lowerLimits.poll();
            high = upperLimits.poll();

            if (root == null) continue;
            val = root.val;
            if (low != null && val <= low) {
                return false;
            }
            if (high != null && val >= high) {
                return false;
            }
            update(root.right, val, high);
            update(root.left, low, val);
        }
        return true;
    }
}
```
