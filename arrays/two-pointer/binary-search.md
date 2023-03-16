# Binary Search

## Strategy

* Divide array in hald and search subarrays for target
* Need midpoint equation mid = left+ (right - left) - 1
* Update window by using mid + 1 or mid - 1

```java
class Solution {
    
    public int search(int[] nums, int target) {
        
        // if (nums.length == 1 && nums[0] != target) {
        //     return -1;
        // }
        int p1 = 0;
        int p2 = nums.length - 1;
        while (p1 <= p2) {
            int mid = p1 + (p2 - p1) / 2;
            if (nums[mid] == target) {
                return mid;
            }
            if (target > nums[mid]) {
                p1 = mid + 1;
            }
        
            if (target < nums[mid]) {
                p2 = mid - 1;
            }
        }
        
        return -1;
    }
}
```

```java
```
