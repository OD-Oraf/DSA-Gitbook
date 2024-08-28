# Min Cost Climbing Stairs

## Strategy - Bottom Up tabulation

*   Recurrence relation

    * `minimumCost[i] = min(minimumCost[i - 1] + cost[i - 1], minimumCost[i - 2] + cost[i - 2])`


* First 2 entries in minCost are 0 because it doesn't  cost anything to reach those steps

### Space/Time

* Time -> O(n)
* Space -> O(n) extra space needed for minCost

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

## Strategy - Top Down Recursion

```java
class Solution {
    private HashMap<Integer, Integer> memo = new HashMap<Integer, Integer>();

    public int minCostClimbingStairs(int[] cost) {
        return minimumCost(cost.length, cost);
    }

    private int minimumCost(int i, int[] cost) {
        // Base case, we are allowed to start at either step 0 or step 1
        if (i <= 1) {
            return 0;
        }

        // Check if we have already calculated minimumCost(i)
        if (memo.containsKey(i)) {
            return memo.get(i);
        }

        // If not, cache the result in our hash map and return it
        int downOne = cost[i - 1] + minimumCost(i - 1, cost);
        int downTwo = cost[i - 2] + minimumCost(i - 2, cost);
        memo.put(i, Math.min(downOne, downTwo));
        return memo.get(i);
    }
}
```
