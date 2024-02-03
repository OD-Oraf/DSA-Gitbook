# House Robber

Link: [https://leetcode.com/problems/house-robber/](https://leetcode.com/problems/house-robber/)

## Strategy - Memoization

```java
class Solution {
    int[] memo;
    public int rob(int[] nums) {
        //create memoization array
        memo = new int[100];
        Arrays.fill(memo, -1);
        return robFrom(0, nums);
        
    }
    
    public int robFrom(int i, int[] nums) {
        if (i > nums.length - 1) {
            return 0; //no more houses to rob
        }
        
        if (memo[i] > -1) {
            return memo[i];//return memorized value
        }
        
        //Recursivve relation for optimal anser
        int ans = Math.max(robFrom(i + 2, nums)+nums[i], robFrom(i + 1, nums));
        
        //cache for future use
        memo[i] = ans;
        return ans;
    }
}
```
