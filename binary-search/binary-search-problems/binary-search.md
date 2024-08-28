# Binary Search

## Strategy

* Divide array in half and search subarrays for target
* Need midpoint equation mid = left+ (right - left) - 1
* Update window by using mid + 1 or mid - 1

### Note-Why is left <= right needed?&#x20;

* Take this example test case \[2,5], target = 5
* The target value is at the right extreme of the array
  * The midpoint will calculate nums\[0] first which is too small
  * If left < right, the logic will terminate since 0 < 1
  * IF the target is at either extreme end of the array then the midpoint will needed to be calculated from right and left being the same values

```java
/*testcase nums = [2,5]
mid = {left+(right-left)/2} -> {0+(1+0)/2} -> 1/2 -> 0 -> NUM[0] = 2 

mid = {left+(right-left)/2} -> {1+(1+1)/2} -> 3/2 -> 1 -> NUM[1] = 5 = target

*/
```

```java
class Solution {
    public int search(int[] nums, int target) {
        int left = 0;
        int right = nums.length - 1;
        
        while (left <= right) {
            int mid = left + (right - left) / 2;
            
            if (nums[mid] == target) {
                return mid;
            } else if (nums[mid] < target) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }
        
        return -1;
        
    }
}
```

