# Number of Islands

## Strategy - DFS

* The idea is to visit each '1'(indication of island) and check the adjacent spots for proof of being an islanf. Set them to 0 to mark visited

```java
class Solution {
    public int numIslands(char[][] grid) {
        // go through each value in the matrix
        
        int count = 0;
        for (int i = 0; i < grid.length; i++) { // row
            for (int j = 0; j < grid[0].length; j++) {// col
                if (grid[i][j] == '1') {
                    dfs(grid, i, j);
                    count++;// a 1 implies that there is at least 1 island
                }
                
            }
            
        }
        
        return count;
        
    }
    
    public void dfs(char[][]grid, int row, int col) {
        // list conditions to skip
        if (// out of bounds conditions
            row < 0 ||
            col < 0 ||
            row >= grid.length || 
            col >= grid[0].length ||
            grid[row][col] == '0'
        ) {
            return;
        }
        
        grid[row][col] = '0'; // mark visited
        dfs(grid, row - 1, col);// up
        dfs(grid, row + 1, col); // down
        dfs(grid, row, col - 1); // left
        dfs(grid, row, col + 1); //right
    }
}
```
