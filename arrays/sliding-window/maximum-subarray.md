---
description: Not really sliding window but it helps me think about the problem
---

# Maximum Subarray

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
  * Even if the next number is negative, it effect will get erased by this step
  * fda

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

## Optimized brute force

* Calculate all subarrays and track best one
* User looop that used each index as the starting point for each subarray
* for each starting point, currentSubarray = 0, loop through from stariting index adding elements to convert subarray&#x20;

```java
class Solution {
    public int maxSubArray(int[] nums) {
        int maxSubarray = Integer.MIN_VALUE;
        for (int i = 0; i < nums.length; i++) {
            int currentSubarray = 0;
            for (int j = i; j < nums.length; j++) {
                currentSubarray += nums[j];
                maxSubarray = Math.max(maxSubarray, currentSubarray);
            }
        }
        
        return maxSubarray;
    }
}


```
