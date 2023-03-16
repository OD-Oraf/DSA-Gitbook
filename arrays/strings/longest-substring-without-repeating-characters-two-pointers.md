# Longest Substring Without repeating characters(Two Pointers)

## Strategy

* HashMap to keep track of character frequency
  * Need map.getOrDefault- if element doesn't already exist then initialize to 0
* If current character is non unique, shorten window

```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        
        HashMap<Character, Integer> map = new HashMap<>();
        int maxLen = 0; 
        int left = 0; // left side of window
        
        // i will be right side of window
        for (int i = 0; i < s.length(); i++) { 
            char c = s.charAt(i);
            map.put(c, map.getOrDefault(c, 0) + 1);
            
            // Shrink window if duplicate found
            while (map.get(c) == 2) {
                char leftChar = s.charAt(left);
                map.put(leftChar, map.get(leftChar) - 1);
                if (map.get(leftChar) == 0) {
                    map.remove(leftChar);
                }
                left++; 
            }
            
            maxLen = Math.max(maxLen, i - left + 1); 
        }
        
        return maxLen;
        
    }
}
```
