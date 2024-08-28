# Max Area if Island

```java
class Solution {
    private int maxArea = 0;
    public int maxAreaOfIsland(int[][] grid) {
        for (int row = 0; row < grid.length; row++) {
            for (int col = 0; col < grid[0].length; col++) {
                maxArea = Math.max(maxArea, getMaxArea(grid, row, col));
            }
        }
        return maxArea;
        
    }
    
    public int getMaxArea(int[][] grid, int row, int col) {
        if (
            row < 0 || 
            col < 0 ||
            row == grid.length ||
            col == grid[0].length ||
            grid[row][col] == 0
        ) {
            return 0;
        }
        
        grid[row][col] = 0;// denote visited coordinate
        
        return (1 + 
                getMaxArea(grid, row + 1, col) + 
                getMaxArea(grid, row - 1, col) + 
                getMaxArea(grid, row, col + 1 ) + 
                getMaxArea(grid, row, col - 1) 
           );
    }
}
```
