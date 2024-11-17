# Same Tree

### Important Code

### Python

```python
# Return for recursicve function
return self.isSameTree(p1, p2)
```

### Java

```java
Queue<TreeNode> queue = new LinkedList<>()
queue.offer()
queue.poll()
```

## Strategy(Recursive)

* Check if trees are null(same
  * return true
* Check if one or other tree is null(different)
  * Return null&#x20;
* Check node values traversal
  * return false if different

## Time Complexity

* Time - O(N)&#x20;
  * Visit each node once
* Space - O(N)
  * Keep stack dequeue

### Recursive Solution

#### Python

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def isSameTree(self, p: Optional[TreeNode], q: Optional[TreeNode]) -> bool:
        if not p and not q:
            return True
        
        if not p or not q:
            return False
        
        if p.val != q.val:
            return False
        
        return self.isSameTree (p.left, q.left) and self.isSameTree(p.right, q.right)
```

#### Java

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
    public boolean isSameTree(TreeNode p, TreeNode q) {
        if (p == null && q == null) {
            return true;
        }
        if (p == null || q == null) {
            return false;
        }
        
        if (p.val != q.val) { // p.val and q.val not needed because first condition will check if we hit the lead nodes
            return false;
        }
        
        return isSameTree(p.left, q.left) && isSameTree(p.right, q.right);
        
    }
}
```

## Iterative Solution

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
    public boolean isSameTree(TreeNode p, TreeNode q) {
        //iterative solution
        Queue<TreeNode> queue = new LinkedList<>();
        queue.offer(p);
        queue.offer(q);
        
        while (!queue.isEmpty()) {
            TreeNode currP = queue.poll();
            TreeNode currQ = queue.poll();
            if (currP == null && currQ == null) {
                continue;
            }
            if (currP == null || currQ == null) {
                return false;
            }
            if (currP.val != currQ.val) {
                return false;
            }
            
            queue.offer(currP.left);
            queue.offer(currQ.left);
            queue.offer(currP.right);
            queue.offer(currQ.right);
        }
        
        return true;
    }
}
```

