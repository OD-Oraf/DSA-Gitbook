# Valid Anagram

### Strategy

* Check for empty strings and unequal string length between both
* Store character counts in hashmap
* Iterate through anagram nad subtract from hashmap

```java
class Solution {
    public boolean isAnagram(String s, String t) {
        // Enter characters into hashmap and keep count
        if (s.length() == 0 || t.length() == 0 || s.length() != t.length()) {
            return false;
        }
        
        HashMap <Character, Integer> map = new HashMap();
        for (int i = 0; i < s.length(); i++) {
            char c = s.charAt(i);
            map.put(c, map.getOrDefault(c, 0) + 1);
        }
        
        for (int i = 0; i < t.length(); i++) {
            char d = t.charAt(i);
            if (!map.containsKey(d)) {
                return false;
            } else {
                map.put(d, map.get(d) - 1);
            }
            
            if (map.get(d) == 0) {
                map.remove(d);
            }
        }
        
        return map.isEmpty();
        
    }
}
```
