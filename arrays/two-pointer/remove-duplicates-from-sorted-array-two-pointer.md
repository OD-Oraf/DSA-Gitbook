# Remove Duplicates from Sorted Array (Two Pointer)

## Strategy

* Use 2 pointer (left, right(int i)). int i in the for-loop will be the right pointer.&#x20;
* &#x20;Left pointer keeps last index of non-duplicates while right finds the next not duplicate.
* Once next duplicate is found, left +  1 will be the next non duplicate and left index is updated.&#x20;

```java
class Solution {
    public int removeDuplicates(int[] nums) {
        // 2 pointer
        int left = 0; 
        
        
        for (int i = 1; i < nums.length; i++) {
            int leftVal = nums[left];
            int rightVal = nums[i];
            
            if (rightVal > leftVal){
                nums[left + 1] = rightVal;
                left++;  
            }   
        }
        return left + 1;
    }
}// Some code
```
