# Squares of a Sorted Array(Two Pointer)

## Strategy

* Create empty array to store squares
* Compare squares and fill array from the back

```java
class Solution {
    public int[] sortedSquares(int[] nums) {
        int left = 0; 
        int right = nums.length - 1;
        int[] squares = new int[nums.length];
        int emptyIndex = nums.length - 1;
        
        while (left <= right) {
            int leftSquared = nums[left] * nums[left];
            int rightSquared = nums[right] * nums[right];
            
            if (leftSquared > rightSquared) {
                squares[emptyIndex] = leftSquared;
                emptyIndex--;
                left++;
            } else {
                squares[emptyIndex] = rightSquared;
                emptyIndex--;
                right--;
            }
        }
        return squares; 
    }
}
```
