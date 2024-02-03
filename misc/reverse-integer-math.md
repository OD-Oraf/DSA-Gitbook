# Reverse Integer(Math)

[https://leetcode.com/problems/reverse-integer/](https://leetcode.com/problems/reverse-integer/)

```java
class Solution {
    public int reverse(int x) {
        int reverse = 0;
        while (x != 0) {
            int pop = x % 10; // get last digit ex. 85 % 10 = 5
            x /= 10;
            
            if (reverse > Integer.MAX_VALUE/10 || (reverse == Integer.MAX_VALUE / 10 && pop > 7)) {
                return 0;
            }
            if (reverse < Integer.MIN_VALUE/10 || (reverse == Integer.MIN_VALUE / 10 && pop < -8)) {
                return 0;
            }
            
            reverse = reverse * 10 + pop;
        }
        
        return reverse;
    }
}
```
