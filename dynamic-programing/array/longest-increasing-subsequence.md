# Longest Increasing Subsequence

## Strategy - Brute Force

* At each value in the array we face 2 choices -> include/exclude from subsequence
* 2 options for each value -> O(2^n)

## Strategy - Dynamic Programming

* Recognize this is a dynamic programming problem
  * Max or min of something
  * Have to make decisions that may depend on previously made decisions

```java
class Solution {
    public int lengthOfLIS(int[] nums) {
        // start with end index
        // valid solution is if nums[i] < nums[j] preserve ascending sequence
        if (nums.length == 1) {
            return 1;
        }
        
        int[] dp = new int[nums.length];
        Arrays.fill(dp, 1);
        int maxLen = 1;
        
        for (int i = nums.length - 1; i >= 0; i--) {//index through array going backwards
            for (int j = i + 1; j < nums.length; j++) {
                if (nums[i] < nums[j]) {
                    dp[i] = Math.max(dp[i], 1 + dp[j]);
                }
            }
            maxLen = Math.max(maxLen, dp[i]);
        }
        return maxLen;
    }
    
}

```
