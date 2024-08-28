# Valid Sudoku

## Strategy - Iterate through rows, colums and squares

* Need to go throuh each row and column and make sure there are no diplicates -> HashSet for each row
* Keys of HashMap&#x20;
  * Note: Each array is a row. col is he same as row index

$$
key = ({r \over 3} , {c \over 3})
$$

```java
class Solution {
    public boolean isValidSudoku(char[][] board) {
        int N = 9;

        // Use hash set to record the status
        HashSet<Character>[] rows = new HashSet[N];
        HashSet<Character>[] cols = new HashSet[N];
        HashSet<Character>[] boxes = new HashSet[N];
        for (int r = 0; r < N; r++) {
            rows[r] = new HashSet<Character>();
            cols[r] = new HashSet<Character>();
            boxes[r] = new HashSet<Character>();
        }

        for (int r = 0; r < N; r++) {
            for (int c = 0; c < N; c++) {
                char val = board[r][c];

                // Check if the position is filled with number
                if (val == '.') {
                    continue;
                }

                // Check the row
                if (rows[r].contains(val)) {
                    return false;
                }
                rows[r].add(val);

                // Check the column
                if (cols[c].contains(val)) {
                    return false;
                }
                cols[c].add(val);

                // Check the box
                int idx = (r / 3) * 3 + c / 3;
                if (boxes[idx].contains(val)) {
                    return false;
                }
                boxes[idx].add(val);
            }
        }
        return true;
    }
}
```

#### # Detailed Explanation with Examples

The formula used to determine the subgrid index in a Sudoku puzzle is:

```java
int idx = (r / 3) * 3 + c / 3;
```

This formula is crucial for mapping each cell in the Sudoku grid to one of the nine 3x3 subgrids. Let's break down why this formula works with specific examples.

**Sudoku Grid Layout**

Consider a 9x9 Sudoku grid, which is divided into 9 subgrids (3x3 each). These subgrids are indexed from 0 to 8 as follows:

```
| 0 | 1 | 2 |
| 3 | 4 | 5 |
| 6 | 7 | 8 |
```

Each cell in the Sudoku grid can be identified by its row (`r`) and column (`c`), both ranging from 0 to 8.

**How the Formula Works**

* **Division by 3**: The expression `r / 3` and `c / 3` divides the row and column indices by 3, effectively categorizing them into three groups (0-2, 3-5, 6-8), each corresponding to the rows and columns of the subgrids.
* **Multiplication by 3**: Multiplying `(r / 3)` by 3 shifts the subgrid row index to the correct starting position of the subgrid in a flat index scale (0, 3, 6).
* **Addition**: Adding `c / 3` offsets this index by the subgrid column, resulting in a flat index from 0 to 8.

#### Examples

1. **Top-left cell (r=0, c=0)**
   * Calculation: `(0 / 3) * 3 + 0 / 3 = 0 * 3 + 0 = 0`
   * Subgrid Index: 0 (Top-left subgrid)
2. **Middle cell (r=4, c=4)**
   * Calculation: `(4 / 3) * 3 + 4 / 3 = 1 * 3 + 1 = 4`
   * Subgrid Index: 4 (Center subgrid)
3. **Bottom-right cell (r=8, c=8)**
   * Calculation: `(8 / 3) * 3 + 8 / 3 = 2 * 3 + 2 = 8`
   * Subgrid Index: 8 (Bottom-right subgrid)

#### Visualizing the Calculation

To further illustrate, consider the cell at (r=5, c=7):

* `r / 3` results in 1 (since 5 falls in the second group of rows for subgrids).
* `c / 3` results in 2 (since 7 falls in the third group of columns for subgrids).
* Thus, `(1 * 3) + 2 = 5`, placing the cell in subgrid index 5.

#### Conclusion

This formula is a concise and efficient way to determine which of the nine subgrids a particular cell belongs to in a Sudoku puzzle. It leverages integer division and basic arithmetic to map a 2D coordinate (row and column) into a 1D subgrid index, which is essential for checking the rules of Sudoku in algorithms, especially when implementing solutions or validations. This understanding is crucial for developing efficient Sudoku solvers or validators that need to check the uniqueness of numbers in each subgrid.
