---
description: https://leetcode.com/problems/permutation-in-string/
---

# Permutation in string

### Strategy - Sort string and compare substrings (Inefficient)

```java
class Solution {
    public boolean checkInclusion(String s1, String s2) {
        
        s1 = sort(s1);
        
        for (int i = 0; i <= s2.length() - s1.length(); i++) {
            if (s1.equals(sort(s2.substring(i, i + s1.length())))) {
                return true;
            } 
        }       
        return false; 
    }
    
    public String sort(String unsorted) {
        char[] chars = unsorted.toCharArray();
        Arrays.sort(chars);
        return new String(chars);
    }
}
```
