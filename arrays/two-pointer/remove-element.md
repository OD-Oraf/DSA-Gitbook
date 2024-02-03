# Remove element

{% embed url="https://leetcode.com/problems/remove-element/" %}

## Strategy&#x20;

* Use 2 poiners
  * Left keeps track of non-val numbers while rith pointer searches for next non-val number
  * Skip number that are equal to the value

```java
class Solution {
    public int removeElement(int[] nums, int val) {
        
        int left = 0;
        for (int right = 0; right < nums.length; right++) {
            if (nums[right] != val) {
                nums[left] = nums[right];
                left++;
            }
        }
        
        return left;
        
    }
}
```
