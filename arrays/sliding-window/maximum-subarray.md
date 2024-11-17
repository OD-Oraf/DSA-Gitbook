---
description: Not really sliding window but it helps me think about the problem
---

# Maximum Subarray

## # Pre code thoughts

* For each number 'x' inside the input array
  * 2 Choices
    * Add 'x' to the window sum
    * Start a new window sum with 'x'
  * When should we start a new running sum with 'x'?
    * When our current window sum is a negative value -> start nw subarray
    * This is because 'x + negative num'  only lowers x and the sum of the current window
      * So we should just start a new subarray at 'x'&#x20;
  * Return sum of contiguous subarray with highest sum

## Strategy - Kadanes Algorithm

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

There is the possibility that the array **only has negative values.** If so, then the max sum will end up being the smallest negative number since the window sum will be set to 0 on each iteration with all negative numbers

## Strategy - Kadane's Algorithm

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

### Strategy - Dynamic Programming(Not space optimized)

```java
class Solution {
    public int maxSubArray(int[] nums) {
        // Initialize our variables using the first element.
        int currentSubarray = nums[0];
        int maxSubarray = nums[0];
        
        // Start with the 2nd element since we already used the first one.
        for (int i = 1; i < nums.length; i++) {
            int num = nums[i];
            // If current_subarray is negative, throw it away. Otherwise, keep adding to it.
            currentSubarray = Math.max(num, currentSubarray + num);
            maxSubarray = Math.max(maxSubarray, currentSubarray);
        }
        
        return maxSubarray;
    }
}
```

## Strategy - Alternative DP

```java
class Solution {
    public int maxSubArray(int[] nums) {
        if (nums.length == 1) {
            return nums[0];
        }
        
        int maxSum = Integer.MIN_VALUE;
        int windowSum = 0;
        
        for (int i = 0; i < nums.length; i++) {
            windowSum = windowSum + nums[i];
            if (nums[i] > windowSum) {
                windowSum = nums[i];
            }
            
            maxSum = Math.max(maxSum, windowSum);
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
