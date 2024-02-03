# Diameter of binary tree

## Strategy(DFS)

* Calculate left and right paths and update diameter by Math.max(diameter, leftHeight + rightHeight)



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
    int diameter;
    public int diameterOfBinaryTree(TreeNode root) {
        diameter = 0;
        findDiameter(root);
        return diameter;
        
    }
    
    public int findDiameter(TreeNode root) {
        if (root == null) {
            return 0;
        }
        
        int leftPath = findDiameter(root.left);
        int rightPath = findDiameter(root.right);
        
        diameter = Math.max(diameter, leftPath + rightPath);
        
            
        return 1 + Math.max(leftPath, rightPath);
    }
}
```

```java
// Some code 
// find diameter is just finding the longest path of the subtree starting at root

   1
  / \
 2   3
/  \
4   5

findDiameter(1)
   findDiameter(2) - //leftPath = 2
      findDiameter(4)
         findDiameter(null)//left
         findDiameter(null)//right
            return 1 + Math.max(0,0)
            diameter = 0
      findDiameter(5)
         findDiameter(null)//left
         findDiameter(null)//right
            diameter = 0
            return 1 + Math.max(0,0)
   findDiameter(3)//rightPath = 1
      findDiameter(null)//left
      findDiameter(null)//right
         diameter = 0
         return 1 + Math.max(0,0)
   diameter = Math.max(diameter, leftPath + rightPath) = 3
   return 1 + Math.max(2,1)
```



## Time Space Complexity

Time: O(N) - Each node visited once

Space- O(N) Size of call stack during DFS related to height of tree
