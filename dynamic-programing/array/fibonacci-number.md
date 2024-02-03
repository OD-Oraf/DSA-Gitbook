# Fibonacci Number

## Strategy - Recursion

* Recurrence Relation - f(n) = f(n - 1) + f(n -2)

```java
public int fib(int n) {
        if (n <= 1) {
            return n;
        }
        return fib(n - 1) + fib(n - 2);
    }
```

## Strategy - Bottom Up using tabulation

* Create a dp array to memoise answers at each step

```java
public int fib(int n) {
        // Create dp array to memoise answeres
        if (n <= 1) {
            return n;
        }
        int[] dp = new int[n + 1];
        dp[0] = 0;
        dp [1] = 1;
        
        for (int i = 2; i <= n; i++) {
            dp[i] = dp[i - 1] + dp[i - 2];
        }
        
        return dp[n];
        
    }
    
```

## Strategy - Top down with Memoisation

```java
class Solution {
    
    HashMap<Integer, Integer> cache = new HashMap(Map.of(0,0,1,1));
    public int fib(int n) {
        if (cache.containsKey(n)) {
            return cache.get(n);
        }
        cache.put(n, fib(n - 1) + fib(n -2));
        return cache.get(n);
    }
}
```

## Iterative bottom up

```java
public int fib(int n) {
        // only keep track of currenbt and previous 2
        if (n <= 1) {
            return n;
        }
        
        int curr = 0;
        int prev1 = 1;
        int prev2 = 0;
        
        for (int i = 2; i <= n; i++) { //update values curr, prev1, prev2
            curr = prev1 + prev2;
            prev2 = prev1;
            prev1 = curr;
        }
        
        return curr;
        
    }
```
