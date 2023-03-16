# Jump Game

## Strategy (Greedy Solution)

* Work backwards
* Set goal to last index and check if index before can reach by i + nums\[i]\(max number of steps) can reach current goal
* If goal makes it to index 0 then there is a path

```java
class Solution {
    public boolean canJump(int[] nums) {
        int goal = nums.length - 1;
        
        for (int i = goal - 1; i >0 0; i--){
             // if current plus max steps can reach current goal
             // set current to new goal
            if (i + nums[i] >= goal) {
                goal = i;
            }
        }
        
        return goal == 0;
        
    }
}
```
