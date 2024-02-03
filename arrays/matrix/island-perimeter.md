---
description: https://leetcode.com/problems/island-perimeter/
---

# Island Perimeter

### Strategy - Simple Counting

* Go through each cell and when you have land cell, subtract 1 for each adjacent land cell. Remember at the border of matrix, there is no land cell

```java
class Solution {
    public int islandPerimeter(int[][] grid) {
        
        int rowLen = grid.length;
        int colLen = grid[0].length;
        
        int up, down, left, right = 0;
        int result = 0;
        
        for (int r = 0; r < rowLen; r++) {
            for (int c = 0; c < colLen; c++) {
                if (grid[r][c] == 1) { // Only act on land elements
                    // UP
                    if (r == 0) {
                        up = 0;
                    } else {
                        up = grid[r - 1][c];
                    }

                    // DOWN
                    if (r == rowLen - 1) {
                        down = 0;
                    } else {
                        down = grid[r + 1][c];
                    }

                    //LEFT 
                    if (c == 0) {
                        left = 0;
                    } else {
                        left = grid[r][c - 1];
                    }

                    //RIGHT
                    if (c == colLen - 1) {
                        right = 0;
                    } else {
                        right = grid[r][c + 1]; 
                    }
                    
                    // Add to result
                    result += 4 - (up + down + left + right);
                    
                }
                
            }
        }
        
        return result;
        
    }
}
```
