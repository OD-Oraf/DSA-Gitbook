# Sum II - Input Array Is Sorted

## Strategy

* Sorted array -> binary search

```java
class Solution {
    public int[] twoSum(int[] numbers, int target) {
        int left = 0; 
        int right = numbers.length - 1;
        
        while (left <= right) {
            int leftVal = numbers[left];
            int rightVal = numbers[right];
            
            if (leftVal + rightVal == target) {
                return new int[]{left + 1, right + 1};
            }
            
            if (leftVal + rightVal > target){
                right--;
            } else{
                left++;
            }
        }
        
        return new int[]{};
    }
}
```
