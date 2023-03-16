# Smallest Subarray with a Greater Sum (Sliding Window)

## Strategy

* Goal is to look for smallest X which means we use Integer.MAX\_VALUE
* Add num and if its greater than the sum try to remove as many items as possible while still being greater than or equal to the sum&#x20;

```java
class Solution {
    public int minSubArrayLen(int target, int[] nums) {
        
        int minLen = Integer.MAX_VALUE;
        int windowSum = 0;
        int left = 0;
        
        for (int i = 0; i < nums.length; i++) {
            windowSum += nums[i]; 
            while (windowSum >= target) {
                minLen = Math.min(minLen, i - left + 1);
                windowSum -= nums[left];
                left++;
            }
        }
        return minLen == Integer.MAX_VALUE ? 0 : minLen;
    }
}
```
