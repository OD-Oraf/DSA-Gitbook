# Palindromic Substrings

## Strategy - Expand around the center

```java
class Solution {
    public int countSubstrings(String s) {
        // expand around center
        if (s.length() == 1) {
            return 1;
        }
        int res = 0;
        
        for (int i = 0; i < s.length(); i++) {
            int left = i;
            int right = i;
            while (left >= 0 && right < s.length() && s.charAt(left) == s.charAt(right)) {
                left--;
                right++;
                res++;
            }
            
            left = i;
            right = i + 1;
            while (left >= 0 && right < s.length() && s.charAt(left) == s.charAt(right)) {
                left--;
                right++;
                res++;
            }
            
        }
        
        return res;
        
    }
}
```
