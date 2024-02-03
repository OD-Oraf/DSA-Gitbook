# Recursion

* Base case
  * The condition under which your recursion stops

```java
// Some code
public int factorial(int n) {
    if (n == 0) {
        return 1;
    }
    return n * factorial(n - 1)
}

/*
Fibonacci number
n = 3 -> final answer is 6

factorial(3) -> 3*factorial(2) = 3*2 = 6
    factorial(2) -> 2*factorial(1) = 2*1 = 2
        factorial(1) -> 1*factorial(0) = 1*1 = 1
            factorial(0) = 1 -> go back up callstack

*/
```
