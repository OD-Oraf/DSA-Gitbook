# Longest Palindrome

```java
class Solution {
    public int longestPalindrome(String s) {
        // Use hashmap 
        int[] charCounts = new int[128];
        int result = 0;
        for (char c: s.toCharArray()) { // populate charCount
            charCounts[c]++; // Count letters by converting to ascii and updating that index
        }
        
        for (Integer charCount : charCounts) {
            result += charCount / 2 * 2;
            if (result % 2 == 0 && charCount % 2 == 1) {
                result += 1;
            }
        }
        
        return result;
        
    }
}
```
