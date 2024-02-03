# Unique paths

Link: [https://leetcode.com/problems/unique-paths/](https://leetcode.com/problems/unique-paths/)

## Strategy - Dynamic Programming

* Give uniquePath(m,n)
  * m -> rows
  * n -> columns

```java
class Solution {
    public int uniquePaths(int m, int n) {
        // each row is the sum of previous previous colum and row element
        //m = rows, n = cols
        int[][] ans = new int[m][n];
        for (int[] arr : ans) {
            Arrays.fill(arr, 1);
        }
        
        for (int row = 1; row < m; row++) {
            for (int col = 1; col < n; col++) {
                ans[row][col] = ans[row - 1][col] + ans[row][col -1];
            }
        }
        
        return ans[m - 1][n - 1];
        
    }
}


/*
[     N
    M[1,2,3],
     [4,5,6],
     [7,8,9],
]
*/
```

## Strategy - Memoization

* Draw tree for visualization&#x20;
  * Think of each node as grid coordinates

```java
class Solution {
  public int uniquePaths(int m, int n) {
    return uniquePathsHelper(m - 1, n - 1, new int[m][n]);
  }
  
  private int uniquePathsHelper(int m, int n, int[][] memo) {
    if (m < 0 || n < 0) {
      return 0;
    } else if (m == 0 || n == 0) {
      return 1;
    } else if (memo[m][n] > 0) {
      return memo[m][n];
    } else {
      memo[m][n] = uniquePathsHelper(m - 1, n, memo) + uniquePathsHelper(m, n - 1, memo);
      return memo[m][n];
    }
  }
} 

```

## Strategy - Bottom up Tabulation

```java
class Solution {
    public int uniquePaths(int m, int n) {
        // bottom up tabulation
        int[][] grid = new int[m][n];
        
        for(int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (i == 0) grid[0][j] = 1; // top row should be 0's
                if (j == 0) grid[i][j] = 1; // first columns should be 0's
                if (i != 0 && j != 0) {
                    int up = grid[i - 1][j];
                    int left = grid[i][j - 1];
                    grid[i][j] = up + left;
                }
            }
        }
        return grid[m - 1][n - 1]; 
    }
}
```
