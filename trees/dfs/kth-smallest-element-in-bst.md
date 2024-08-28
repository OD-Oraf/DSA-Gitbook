# Kth smallest element in BST

## Strategy - Recursion

* Since the given tree is a binary search tree, to get the elements in order we can do in-order traversal
* During that traversal add the node value to an array
* At the end grab the k-1 index from the array

```java

class Solution {
    public int kthSmallest(TreeNode root, int k) {
        // Use inorder traversal to get and add to array to get elements in order 
        ArrayList<Integer> nums = inorder(root, new ArrayList<Integer>());
        return nums.get(k -1); // Account for 0-index
    }
    
    public ArrayList<Integer> inorder(TreeNode root, ArrayList<Integer> nums) {
        if (root == null) {
            return nums; // GO back up call stack
        }
        
        inorder(root.left, nums);
        nums.add(root.val);
        inorder(root.right, nums);
        
        return nums; // GO Back up callstack
    }
}
```

## Strategy - Iterative(Faster)&#x20;

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
    public int kthSmallest(TreeNode root, int k) {
        // Iterative solution
        // Use a stack to add elements- at the step where we would normally process the node value remove the top of the stack k times. Through we can find the root kth smallest element becaue it will be on top of the stack once we remove k times
        
        LinkedList<TreeNode> stack = new LinkedList<>();
        
        while (root != null || !stack.isEmpty()) {
            while (root != null) {
                stack.push(root);
                root = root.left;
            }
            root = stack.pop();
            k--;
            
            if (k == 0) {
                break;
            }
            root = root.right;
        }
        
        return root.val;
    }
    
    
}
```
