# Longest Sub-string Without repeating characters

## Strategy - Sliding Window

* HashMap to keep track of character frequency
  * Need map.getOrDefault- if element doesn't already exist then initialize to 0
* If current character is non unique, shorten window

### Common mistake&#x20;

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
                char leftChar = s.charAt(left); // Remember to char at front of window not current char
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

### Strategy - Sliding Window optimized&#x20;

```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        
        
        // Optomized sliding window
        HashMap<Character, Integer> map = new HashMap();
        int maxLen = 0;
        int left = 0;
        
        for (int i = 0; i < s.length(); i++) {
            char c = s.charAt(i);
            if (map.containsKey(c)) { // Duplicate condition
                left = Math.max(left, map.get(c));
            }
            
            maxLen = Math.max(maxLen, i - left + 1);
            map.put(c, i + 1);
        }
        
        return maxLen; 
        
    }
}
```
