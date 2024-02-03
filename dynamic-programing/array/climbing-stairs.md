# Climbing Stairs

Link: [https://leetcode.com/problems/climbing-stairs/](https://leetcode.com/problems/climbing-stairs/)

## Strategy - Memoisation

Think of climbing as potentials pathways to get to the target which is climb(n,n)

Can think of climbing as climb(steps-taken,target)

```java
class Solution {
    public int climbStairs(int n) {
        // How many ways can we reach n steps taking only 1 or 2 steps at atime
        int[] memo = new int[n + 1];
        return countPaths(0, n, memo);
    }
    
    public int countPaths(int current, int target, int[] memo) {
        if (current > target) {
            return 0; // not valid path
        }
        
        if (current == target) {
            return 1;//valid path
        }
        
        if (memo[current] > 0) {
            return memo[current];
        }
        
        memo[current] = countPaths(current+1, target, memo) + countPaths(current+2,target, memo);
        return memo[current];
    }
}
```

### dStrategy - Brute force&#x20;

* Base cases
  * i = current steps, n = ammount of steps to be valid path
  * If i larger than n it is an invalid path because we've taken more steps than allowed
  * if i == n, then it is a valid path to n steps

#### Time complexity

* Time - O(2^n)
* Space - O(n)

```java
class Solution {
    public int climbStairs(int n) {
        
        // brute force solution
        return climb(0, n);
    }
    
    public int climb(int i, int n) {
       
        if (i > n) { // overstep n, invalid path
           return 0;  
        }
        
        if (i == n) { // valid path
            return 1;
        }
        
        return climb(i + 1, n) + climb(i + 2, n);
    }
}
```

### Strategy - Dynamic Programming

```java
public class Solution {
    public int climbStairs(int n) {
        if (n == 1) {
            return 1;
        }
        int[] dp = new int[n + 1];
        dp[1] = 1;
        dp[2] = 2;
        for (int i = 3; i <= n; i++) {
            dp[i] = dp[i - 1] + dp[i - 2];
        }
        return dp[n];
    }
}
```
