# Binary Tree Level Order Traversal

## Strategy(Use a queue)

* Setup result as List\<List\<Integer>>
* First offer root into queue(will server as first level)
  * Front of queue is removed its children are added
* Add resulting level into result



> Psudo-code
>
> ```
> printLevelorder(tree)
> 1) Create an empty queue q
> 2) temp_node = root /*start from root*/
> 3) Loop while temp_node is not NULL
>     a) print temp_node->data.
>     b) Enqueue temp_node’s children 
>       (first left then right children) to q
>     c) Dequeue a node from q.
> ```

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
    public List<List<Integer>> levelOrder(TreeNode root) {
        
        List<List<Integer>> result = new ArrayList<>();
        if (root == null) {
            return result;
        }
        
        Queue<TreeNode> queue = new LinkedList<>();
        queue.offer(root); 
        
        while(!queue.isEmpty()) {
            int levelSize = queue.size();
            List<Integer> currentLevel = new ArrayList<>(levelSize);
            
            for (int i = 0; i < levelSize; i++) { // traverse all nodes in each level
                TreeNode currentNode = queue.poll();
                currentLevel.add(currentNode.val);
                if (currentNode.left != null) {
                    queue.offer(currentNode.left);
                }
                if (currentNode.right != null) {
                    queue.offer(currentNode.right);
                }
            }
            result.add(currentLevel);
        }
        return result;
    }
    
}
```
