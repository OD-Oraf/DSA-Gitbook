# Jump Game

## Strategy (Greedy Solution)

* Work backwards
* Set goal to last index and check if index before can reach by i + nums\[i]\(max number of steps) can reach current goal
* If goal makes it to index 0 then there is a path

### Time complexity&#x20;



* Time - O(n)&#x20;
  * Visit each position of the array once
* Space - O(n)
  * Not using any extra space

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

```java
class Solution {
    public boolean canJump(int[] nums) {
        //go backwards
        int goal = nums.length - 1;
        for (int i = goal; i > 0; i--) {
            if (nums[i - 1] + (i - 1) >= goal) {
                goal = i - 1;
            } else {
                continue;
            }
        }
        return goal == 0; 
    }
    
    public boolean canJump(int[] nums) {
        int goal = nums.length - 1;
        for (int i = nums.length - 2; i >= 0; i--) {
            if (nums[i] + i >= goal) {
                goal = i;  
            }
        }

        if (goal == 0) {
            return true;
        } else {
            return false;
        }
        
    }
}
```
