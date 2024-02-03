# Find Minimum in Rotated Sorted Array

```java
class Solution {
    public int findMin(int[] nums) {
        /* 
        If array is unrotated or fully rotatoed the smallest
        element is at the beginning of the array and the left 
        will be greater than the right unless the smallest 
        element returns to first place
        
        The main idea is that we're looking for the pivot point
        
        */ 
        
        int left = 0;
        int right = nums.length - 1;
        while (left <= right) {
            if (nums[left] <= nums[right]) {
                return nums[left];
            }
            
            int mid = (right + left) / 2;
            if (nums[left] <= nums[mid]) {//same partition
                left = mid + 1;
            } else {
                right = mid;
            }
        }
        
        return Integer.MAX_VALUE;
        
    }
}
```
