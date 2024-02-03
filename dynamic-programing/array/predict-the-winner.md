# Predict the Winner



<figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

### Time - Space

Time -> O(2^n)

Space -> O(n)&#x20;

```java
class Solution {
    public boolean predictTheWinner(int[] nums) {
        return maxDiff(nums, 0 , nums.length - 1) >= 0;
        
    }
    
    private int maxDiff(int[] nums, int l, int r) {
        if (l > r) {
            return 0;
        }
        
        int left = nums[l] - maxDiff(nums, l+1, r);
        int right = nums[r] - maxDiff(nums, l, r-1);
        
        return Math.max(left, right);
    }
}
```
