# Pascal's Triangle

Link: [https://leetcode.com/problems/pascals-triangle/](https://leetcode.com/problems/pascals-triangle/)

## Strategy

* Why dynamic programming?
  * Optimal substructure
  * Overlapping subproblems
* Dynanic porogramming Framework
  * Base Case: Value at beginning and end is always 1
  * Recurrence Relation: Each number is the sum if the numbers above it
    * Sum = previous row, previous columns + previous row current column
    * Triangle\[row,col] = triangle\[row-1]\[col-1] + triangle\[row-1]\[col]

```java
class Solution {
    public List<List<Integer>> generate(int numRows) {
        List<List<Integer>> res = new ArrayList<>();
        res.add(new ArrayList<>());
        res.get(0).add(1);

        for (int row = 1; row < numRows; row++){
            List<Integer> currRow = new ArrayList<>();
            List<Integer> prevRow = res.get(row - 1);

            currRow.add(1);

            for(int col = 1; col < row; col++) { //col < row because the row length is equal to the row number
                int sum = prevRow.get(col - 1) + prevRow.get(col);
                currRow.add(sum);
            }
            currRow.add(1);
            res.add(currRow);
        }

        return res;

    }
}
```
