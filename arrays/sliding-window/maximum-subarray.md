---
description: Not really sliding window but it helps me think about the problem
---

# Maximum Subarray

## Strategy

* Kadanes algorithm
  * Set up maxSum and windowSum
  * Keep adding nums\[i] to windowSum unless nums\[i] > windowSum
    * If this is the case nums\[i] becomes the new windowSum
  * Compare windowSum and maxSum and store that as the maxSum
  * Return maxSum

## The gotcha

* maxSum and windowSum need to be set to nums\[0] and loop needs to start at 1
* if nums == \[-1] the maxSum will return as 0 and not -1
* Also if loop starts at 0 it will ad first number twice

```java
class Solution {
    public int maxSubArray(int[] nums) {
        // Sliding window
        
        /*
        Keep Track of : 
        left pointer
        maxSum
        */
        
        int maxSum = nums[0]; 
        int windowSum = nums[0];
        
        for (int i = 1; i < nums.length; i++) {
            windowSum += nums[i];
            if (nums[i] > windowSum) {
                windowSum = nums[i];
            }
            maxSum = Math.max(maxSum, windowSum);
        }
        return maxSum;
    }
}
```
