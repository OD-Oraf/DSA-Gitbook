# Valid Palindrome

## Strategy

* Use two pointer strategy
* Remember to&#x20;
  * Lowercase characters
  * Ignore elements that aren't a letter



```java
class Solution {
    public boolean isPalindrome(String s) {
        // Use two pointers at start and end of word
        
        // EIther empty or one character
        if (s.length() <= 1) {
            return true;
        }
        
        s.toLowerCase();
        
        int p1 = 0;
        int p2 = s.length() - 1;
        // make lowercase
        
        while (p1 < p2) {
            char start = Character.toLowerCase(s.charAt(p1));
            char end = Character.toLowerCase(s.charAt(p2));
            
            if (!Character.isLetterOrDigit(start)) {
                p1++;
                continue;
            }
            if (!Character.isLetterOrDigit(end)) {
                p2--;
                continue;
            }
            
            if (start != end) {
                return false;
            }
            p1++;
            p2--;
        }
        
        return true;
        
    }
}
```
