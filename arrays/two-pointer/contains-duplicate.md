# Contains Duplicate

## Strategy

* Cab soirt array and check but very slow
* Can also use hashmap to check for duplicates

```java
class Solution {
    public boolean containsDuplicate(int[] nums) {
        if (nums.length == 1) {
            return false;
        }
        
        Arrays.sort(nums);
        
        for (int i = 0; i < nums.length - 1; i++) {
            if (nums[i] == nums [i + 1]) {
                return true;
            }
        }
        
        return false;
        
    }
}
```
