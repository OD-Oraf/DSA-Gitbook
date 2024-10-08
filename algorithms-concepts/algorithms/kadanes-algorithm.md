# Kadanes Algorithm

## Used to solve the max subarray problem

## Strategy

* Kadanes algorithm
  * Set up maxSum and windowSum
  * Keep adding nums\[i] to windowSum unless nums\[i] > windowSum
    * If this is the case, nums\[i] becomes the new windowSum
  * Compare windowSum and maxSum and store that as the maxSum
  * Return maxSum

## The gotcha

* maxSum and windowSum need to be set to nums\[0] and loop needs to start at 1
* If nums only has one element, return nums\[0] not 0
  * because if nums\[0] == \[-1] the maxSum will return as 0 and not -1
* Also if loop starts at 0 it will add first number twice
* Any time the sum dips below 0, reset the current sum to 0
  * This way negative numbers cant drag down the next positive number
  * Even if the next number is negative, its effect will get erased by this step

### Why set maxSum to Integer.MIN\_VALUE?

There is the possibility that the array only has negative values. If so, then the max sum will end up being the smallest negative number since the window sum will be set to 0 on each iteration with all negative numbers

```java
class Solution {
    public int maxSubArray(int[] nums) {
        // Kadanes algorithm
        // Take max of currSum and maxSUm
        // if currSum falls under 0, set it to 0
        if (nums.length == 1) {
            return nums[0];
        }
        
        int currSum = 0;
        int maxSum = Integer.MIN_VALUE;
        
        for (int i = 0; i < nums.length; i++) {
            currSum += nums[i];
            maxSum = Math.max(maxSum, currSum);
            
            if (currSum < 0) {
                currSum = 0;
            }
        }
        
        return maxSum;
    }
}
```
