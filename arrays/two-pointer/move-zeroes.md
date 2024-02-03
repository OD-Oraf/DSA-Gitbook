# Move Zeroes

### Strategy(Two pointers)

* Use two pointers and use right pointers to swap non-zero values with left pointer zero values
* Use temp values to do swapping or you doubple swap values

```java
class Solution {
    public void moveZeroes(int[] nums) {
        // Use 2 pointers, left for non 0 array right to search for next non 0 
        int left = 0;
        
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] != 0){ // once we find non 0 - swap
                int temp = nums[left];
                nums[left] = nums[i];
                nums[i] = temp;
                
                left++;
            }
        }
            
    }
}


// [0,1,0,3,12]
```
