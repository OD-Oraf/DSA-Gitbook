# 3 Sum smaller

## Two Pointer method

```java
class Solution {
    int count = 0;
    public int threeSumSmaller(int[] nums, int target) {
        if (nums.length < 3) {
            return 0;
        }
        
        Arrays.sort(nums);
        
        for(int i =  0; i < nums.length - 2; i++) {
            int left = i + 1;
            int right = nums.length - 1;
            while (left < right) {
                if (nums[i] + nums[left] + nums[right] < target) {
                    count += right - left;
                    left++;
                } else {
                    right--;
                }
            }
        }
        return count;
    }
}
```

### Time/Space

Time-O(n^2)

* Sorting arrays -> O(nlog(n))
* Loop that touches (n-2) elements
* Overall time complexity is O(nlog(n) + n^2) -> O(n^2)

Space -> O(1) -> no additional data structures used
