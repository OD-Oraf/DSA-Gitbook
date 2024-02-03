# Product of Array Except Self

## Strategy - prefix and postfix arrays

* Traverse the array twice, forwards and backwards
* Create prefix product array by multiplying the last index of nums  by the previous prefix product
* Create suffix product array by doing the same in reverse at the end of the nums array

### Time complexity -&#x20;

* Time - O(n)
  * Traversing array twice so more like O(2n)
* Space - O(n)&#x20;
  * Using extra space for prefix and postfix arrays

```java
class Solution {
    public int[] productExceptSelf(int[] nums) {
        
        
        int[] leftPrefix = new int[nums.length];
        int[] rightPostfix = new int[nums.length];
        int[] ans = new int[nums.length];
        
        //construct left prefix array
        leftPrefix[0] = 1;
        for (int i = 1; i < nums.length; i++) {
            leftPrefix[i] = leftPrefix[i - 1] * nums[i - 1];
        }
        
        //construct right postfix array
        rightPostfix[nums.length - 1] = 1;
        for (int i = nums.length - 2; i >= 0; i--){
            rightPostfix[i] = rightPostfix[i + 1] * nums[i + 1];
        }
        
        //ans array
        for (int i = 0; i < nums.length; i++) {
            ans[i] = leftPrefix[i] * rightPostfix[i];
        }
        
        return ans;
    }
}
```
