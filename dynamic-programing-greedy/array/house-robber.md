# House Robber

Link: [https://leetcode.com/problems/house-robber/](https://leetcode.com/problems/house-robber/)

* [https://leetcode.com/problems/house-robber/discuss/156523/From-good-to-great.-How-to-approach-most-of-DP-problems.](https://leetcode.com/problems/house-robber/discuss/156523/From-good-to-great.-How-to-approach-most-of-DP-problems.)
* [https://www.youtube.com/watch?v=VXqUQYGMnQg\&t=101s](https://www.youtube.com/watch?v=VXqUQYGMnQg\&t=101s)

## Strategy - Memoization



<pre class="language-java"><code class="lang-java">/*
    toatal loot at n = MAX(total_loot[n - 2] + loot[n], total_loot[n - 1]) 
    nums(loot)       = 2,7,3,1,4 ,2 ,1 ,8
    memo(total_loot) = 2,7,7,8,11,11,12,19
*/


<strong>class Solution {
</strong>    int[] memo;
    public int rob(int[] nums) {
        //create memoization array
        memo = new int[nums.length + 1];
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

</code></pre>

### Time and Space:&#x20;

* Time
  * O(n) -> Length of input array
  * O(n) -> O(n) + O(n)
    * O(n) -> Call stack memory
    * O(n) -> Memo array

## Tabulation Dynamic Programming

```java
class Solution {
    
    public int rob(int[] nums) {
        if (nums.length < 2) {
          return nums[0]; // If only 1 element, just return it
        }
        int[] dp = new int[nums.length]; // Create array to store the maximum loot at each index

        dp[0] = nums[0];// Memoize maximum loots at first 2 indexes
        dp[1] = Math.max(nums[0], nums[1]);

        // Use them to fill complete array
        for (int i = 2; i < nums.length; i++) {
          // Core logic
          dp[i] = Math.max(dp[i - 2] + nums[i], dp[i - 1]);
        }

        return dp[nums.length - 1];
  }

}
```
