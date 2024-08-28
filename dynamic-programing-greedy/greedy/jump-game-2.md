# Jump Game 2

[https://leetcode.com/problems/jump-game-ii/discuss/18014/Concise-O(n)-one-loop-JAVA-solution-based-on-Greedy](https://leetcode.com/problems/jump-game-ii/discuss/18014/Concise-O\(n\)-one-loop-JAVA-solution-based-on-Greedy)

```java
class Solution {
    public boolean canJump(int[] nums) {
        // Go backwards and see how we can reach the last index
        if (nums.length == 1) {
            return true;
        }
        int validEnd = nums.length - 1;
        
        for (int i = nums.length - 2; i >= 0; i--) {
            if (nums[i] + i >= validEnd) {
                validEnd = i;
            }
        }
        
        return validEnd == 0;
        
    }
}
```
