# Palindrome Number

## Strategy

* Remember
  * Negative numbers cant be revered
  * Numbers ending in 0(divisible by 10) cant be reversed&#x20;
* Process for reversing number (only reversing half the number )
  * Get last digit from x by % 10
  * Pop last digit by /= 10
  * Move number into right place by multiplying by 10 and adding last digit
* True conditions
  * If x and reversed are equal. Will occur if there are an even number of digits
  * x == reversed / 10 accounts for numbers with odd digits, this will pop middle digit and check for equivalency &#x20;

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

Easier to understand but less efficient

```java
class Solution {
    public boolean isPalindrome(int x) {
        
        
        // If negative, it cant be reversed
        if (x < 0){
            return false;
        }
        
        int number = x;
        
        int reverse = 0;
        
        while(number > 0) {
            // Handle digit palceing and adding last digit from original number
            reverse = reverse * 10 + number % 10;
            number /= 10;
        }
        return x == reverse;
    }
}
```
