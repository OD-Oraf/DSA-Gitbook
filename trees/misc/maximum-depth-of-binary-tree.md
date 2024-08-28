# Maximum Depth of binary tree

### Strategy - Recursion

* Take max path of each tree. Add one to return statement so every recursive call will keep track of the depth

```java
// Recursive solution
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
        
        if (root == null) {
            return 0;
        } else {
            int left = maxDepth(root.left);
            int right = maxDepth(root.right);
            return 1 + Math.max(left, right);
        } 
    }
}
```

```java
// Excample 
root = [3,9,20,null,null,15,7]

    3
   / \
  9  20
     / \
    15  7
    
maxDepth(3) = 3
   left:maxDepth(9) = 1
      left:maxDepth(null) -> 0
      right:maxDepth(null) -> 0
      return 1 + Math.max(0,0) = 1
   right:naxDepth(20) = 2
      left:maxDepth(15) = 1
         left:maxDepth(null) -> 0
         right:maxDepth(null) -> 0
         return 1 + Math.max(0,0) = 1
      right:maxDepth(7) = 1
         left:maxDepth(null) -> 0
         right:maxDepth(null) -> 0
         return 1 + Math.max(0,0) -> 1
      return 1 + Math.max(1,1) -> 2
   return 1 + Math.max(1,2) -> 3
             
```

### Time/Space

* Time O(n) -> Visit each node exactly once
* Space O(n) -> unbalanced tree
  * O(log(n)) -> Balanced tree&#x20;

## Strategy - BFS(Count levels)

```java
class Solution {
    public int maxDepth(TreeNode root) {
    if(root == null) {
        return 0;
    }
    Queue<TreeNode> queue = new LinkedList<>();
    queue.offer(root);
    int count = 0;
    while(!queue.isEmpty()) {
        int size = queue.size();
        while(size-- > 0) {
            TreeNode node = queue.poll();
            if(node.left != null) {
                queue.offer(node.left);
            }
            if(node.right != null) {
                queue.offer(node.right);
            }
        }
        count++;
    }
    return count;
}
}
```
