# Longest Palindromic Substring

### Strategy - Expand around center

* Think of outward spread from each index. Make sure to account for even and odd palindromes. Even: left = i, right = i Odd: left = i, right = 1 + 1

### Time complexity

* Time - O(n^2)
  * Using while  look within for loop
* Space - O(1)

```java
class Solution {
    public String longestPalindrome(String s) {
        // Compute palindrom with current index as the center
        String res = "";
        int resLen = 0;v
        
        for (int i = 0; i < s.length(); i++) {
            // for odd len palindromes
            int left = i;
            int right = i;
            while (left >= 0 && right < s.length() && s.charAt(left) == s.charAt(right)) {
                if ((right - left + 1) > resLen) {
                    res = s.substring(left, right + 1);
                    resLen = (right - left) + 1;
                }
                left--;
                right++;
            }
            
            // for even len palindromes
            left = i;
            right = i + 1;
            while (left >= 0 && right < s.length() && s.charAt(left) == s.charAt(right)) {
                if ((right - left + 1) > resLen) {
                    res = s.substring(left, right + 1);
                    resLen = (right - left) + 1;
                }
                left--;
                right++;
            }
        }
        
        return res; 
        
    }
}
```
