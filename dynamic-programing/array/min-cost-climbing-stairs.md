# Min Cost Climbing Stairs

## Strategy - Bottom UP tabulation

*   Recurrence relation

    * `minimumCost[i] = min(minimumCost[i - 1] + cost[i - 1], minimumCost[i - 2] + cost[i - 2])`


* First 2 entries in minCost are 0 because it doesnt  cost anything to reach those steps

```java
class Solution {
    public int minCostClimbingStairs(int[] cost) {
        
        int[] minCost = new int[cost.length + 1];//last index represents top floor
        Arrays.fill(minCost, 0);
        
        for (int i = 2; i < minCost.length; i++) {
            //min cost to reach previous step + cost of step to reach current
            int oneStep = minCost[i - 1] + cost[i - 1];
            int twoStep = minCost[i - 2] + cost[i - 2];
            //store min of oneStep and twoStewp
            minCost[i] = Math.min(oneStep, twoStep);
        }
        
        return minCost[minCost.length - 1];
        
    }
}
```
