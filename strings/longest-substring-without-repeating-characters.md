# Longest Substring without repeating Characters

## Strategy

* Sliding window pattern
* Whenever we have duplicate character in window remove it by updating map count and left pointer
* Remember i - left + 1 to account for index starting at 0

```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        // Use hashmap to keep track of elemenets in string
        if (s == "") {
            return 0;
        } else if (s.length() == 1) {
            return 1;
        }
        
        HashMap<Character, Integer> map = new HashMap<>();
        int left = 0;
        // int right = 0;
        int maxLength = 0;
        
        for (int i = 0; i < s.length(); i++) {
            char c = s.charAt(i);
            map.put(c, map.getOrDefault(c, 0) + 1);
            
            while (map.get(c) > 1) {
                char leftChar = s.charAt(left);
                map.put(leftChar, map.get(leftChar) - 1);
                if (map.get(leftChar) == 0) {
                    map.remove(leftChar);
                }
                left++;   
            }
            maxLength = Math.max(maxLength, i - left + 1);  
        }
        return maxLength;
    }
}
```

