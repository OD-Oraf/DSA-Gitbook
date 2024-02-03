# Happy Number

```java
class Solution {
    public boolean isPalindrome(int x) {
        
        // 0 will laways bew a palindrome
        if (x == 0) {
            return true;
        }
        // negatives and multiples of 10 cant be reversed
        if (x < 0 || x % 10 == 0) {
            return false;
        }
        
        int reversed = 0;
        while (x > reversed) {
            int lastDigit = x % 10;
            x /= 10;
            reversed = (reversed * 10) + lastDigit;
        }
        
        if (x == reversed || x == reversed /10) {
            return true;
        } else {
            return false;
        }
        
    }
}
```
