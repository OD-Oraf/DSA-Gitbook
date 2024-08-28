# Dynamic Programming

## Memoization vs Tablulation

* Top Down(Caching or memoization)
  * Break down main problem into subproblems and solve recursively&#x20;
  * Need to figure out recursive relation
* Bottom Up(Tabulation)
  * Use base cases to solve subproblems and build to the final solution
  * Filling up table -> solution is in the last entry of the table
  * Benefits
    * No recursion
    * Refer to previous entries in the table and compute iteratively&#x20;



## Memoization Recipe

1. Make it works
   1. Visualize problem as a tree(dfs?)
   2. Implement tree using recursion
   3. Test it
2. Make it efficient
   1. Add memo object
   2. Add base case to return memo values
   3. Store return values into memo
