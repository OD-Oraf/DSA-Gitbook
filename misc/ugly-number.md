# Ugly Number

## Strategy - Keep Dividing number until it either becomes 0 or 1

* 0 Means that it is not evenly divisible by the allowed numbers
* 1 means that it is evenly divisible by one of the allowed numbers

```java
class Solution {
    public boolean isUgly(int n) {
        while (n > 1) {
            if (n % 2 == 0) n /= 2;
            else if (n % 3 == 0) n /= 3;
            else if (n % 5 == 0) n /= 5;
            else return false;
        }
        return n > 0;
    }
}
```
