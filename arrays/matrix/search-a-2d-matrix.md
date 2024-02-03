# Search a 2D matrix

Links: [https://leetcode.com/problems/search-a-2d-matrix/](https://leetcode.com/problems/search-a-2d-matrix/)

```java
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        int m = matrix.length;// number of rows
        if (m == 0)
            return false;
        int n = matrix[0].length;// number of colums(or number in each row)

        // binary search
        int left = 0;
        int right = m * n - 1; //length if was array 
        int pivotIdx, pivotElement;
        
        //binary earch
        while (left <= right) {
            pivotIdx = (left + right) / 2;
            pivotElement = matrix[pivotIdx / n][pivotIdx % n];
            if (target == pivotElement)
                return true;
            else {
                if (target < pivotElement)
                    right = pivotIdx - 1;
                else
                    left = pivotIdx + 1;
            }
        }
        return false;
    }
}
```
