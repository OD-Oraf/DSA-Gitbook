# Search in Rotated Sorted Array

```java
class Solution {
    public int search(int[] nums, int target) {
    int left = 0;
    int right = nums.length - 1;
    while (left <= right) {
        int mid = left + (right - left) / 2;
        if (nums[mid] == target) {
            return mid;
        } else if (nums[mid] > target) {
            // the left half strictly increasing, target still greater
            if (nums[left] <= nums[mid] && nums[left] > target) { //set boundary for other partition
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        } else {
            // the right part strictly increasing and target is still less
            if (nums[right] >= nums[mid] && nums[right] < target) { //set boundary for other partition
                right = mid - 1;
            } else {
                left = mid + 1;
            }
        }
    }
    return -1;
}
}
```
