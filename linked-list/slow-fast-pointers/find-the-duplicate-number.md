# Find the Duplicate Number

[https://leetcode.com/problems/find-the-duplicate-number/](https://leetcode.com/problems/find-the-duplicate-number/)

## Strategy(Find linked list cycle)

The idea is to reduce the problem to a linked list cycle

f(x) = nums\[x]

Example

```
index  |0|1|2|3|4|5|6|
nums   |2|6|4|1|3|1|5|

nums[2] = 4
nums[4] = 3
nums[3] = 1
nums[1] = 6
nums[6] = 5
nums[5] = 1 -> cycle
```

&#x20;This algorithm consists of two parts

* Find the intersection
* Find where the cycle beings

```java
class Solution {
    public int findDuplicate(int[] nums) {
        
        int slow = nums[0];
        int fast = nums[0];
        
        do {// do this way to prevent skip due to slow and fast being the same at the beginning 
    
            slow = nums[slow];
            fast = nums[nums[fast]];
        } while (slow != fast);
        
        slow = nums[0];
        
        while (slow != fast) {
            slow = nums[slow];
            fast = nums[fast];
        }
        
        return slow;
        
    }
}
```
