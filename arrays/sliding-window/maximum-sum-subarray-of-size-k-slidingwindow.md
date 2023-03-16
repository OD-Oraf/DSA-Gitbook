# Maximum Sum Subarray of Size K(SlidingWindow)

## Strategy

* Compare window sum + num and num. If num is greater than the window sum plus then num becomes the new window sum and window resets.&#x20;

```java
class Solution {
    public int maxSubArray(int[] nums) {  
        int windowSum = nums[0];
        int maxSum = nums[0];
        
        for (int i = 1; i < nums.length; i++) {
            
            windowSum = Math.max(windowSum + nums[i], nums[i]);
            maxSum = Math.max(maxSum, windowSum);
        }
        return maxSum;     
    }
}
```
