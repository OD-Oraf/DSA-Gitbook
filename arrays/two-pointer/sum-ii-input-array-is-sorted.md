---
description: https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/
---

# Sum II - Input Array Is Sorted

## Strategy - Two pointers

* Use two pointers at both ends and update left and right indicies based on value of sum vs target

```java
class Solution {
    public int[] twoSum(int[] numbers, int target) {
        // Use two points going inwards
        // if too large slide right inwards
        // iff too small slide left inward 
        
        int left = 0; 
        int right = numbers.length - 1;
        
        while (left <= right) {
            int leftInt = numbers[left];
            int rightInt = numbers[right];
            
            if (leftInt + rightInt > target) {
                right--;
                continue;
            } else if (leftInt + rightInt < target) {
                left++;
                continue;
            } else {
                return new int[] {left + 1, right + 1};
            }
        }
        
        return null;
        
        
    }
}
```
