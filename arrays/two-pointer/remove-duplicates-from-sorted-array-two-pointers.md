# Remove Duplicates from Sorted Array(two pointers)

## ConStrategy

* Left pointer keeps track of sorted values. Right searches for next non-duplicate

```java
class Solution {
    public int removeDuplicates(int[] nums) {
        int left = 0;
        for (int i = 0; i < nums.length; i++) {
            if (nums[left] == nums[i]) {
                continue;
            }
            nums[left + 1] = nums[i];
            left++; 
        }
        return left + 1; 
    }
}
```

```java
class Solution {
    public int removeDuplicates(int[] nums) {
        // left pointer keeps track of sorted
        // right pointer searches for next unique and switches with left + 1
        
        if (nums.length == 1) {
            return 1;
        }
        int numsLen = nums.length;
        int left = 0;
        int right = 0;
        
        while (right < numsLen) {
            int leftVal = nums[left];
            int rightVal = nums[right];
            if (rightVal == leftVal) {
                right++;
            } else {
                nums[left + 1] = rightVal;
                left++;
            }
        }
        
        return left + 1;
        
    }
}

```
