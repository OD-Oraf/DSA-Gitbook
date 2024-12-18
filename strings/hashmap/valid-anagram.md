# Valid Anagram

### Strategy - Character Count via HashMap

* Check for empty strings and unequal string length between both
* Store character counts in hashmap
* Iterate through anagram and subtract from hashmap

#### Python

```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        #Get character count using hashmap
        if len(s) != len(t):
            return False
        #Create hashmap
        hashmap = {}
        
        #Get hashmap character count
        for char in s:
            hashmap[char] = hashmap.get(char, 0) + 1

        '''
        Remove characters as we find them in t,
        - If char not found in hashmap then reutrn false
        '''
        
        for char in t:
            if char in hashmap:
                hashmap[char] = hashmap.get(char) - 1
                if hashmap[char] == 0:
                    hashmap.pop(char)
            else:
                return False

        if len(hashmap) == 0:
            return True
            
        
```

#### Java

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

## Strategy - Frequency Counter with arrays

```java
public boolean isAnagram(String s, String t) {
    if (s.length() != t.length()) {
        return false;
    }
    int[] counter = new int[26];
    for (int i = 0; i < s.length(); i++) {
        counter[s.charAt(i) - 'a']++;
        counter[t.charAt(i) - 'a']--;
    }
    for (int count : counter) {
        if (count != 0) {
            return false;
        }
    }
    return true;
}
```

## Strategy - Sorting

### Time Complexity&#x20;

* O(n log n) - Sorting algorithm

### Space Complexity

* O(1) depending on sorting algorithm
* O (n) - Java uses extra space for converting to char array

```java
class Solution {
    public boolean isAnagram(String s, String t) {
        if (s.length() != t.length()) {
            return false;
        }
        
        char[] sArr = s.toCharArray();
        char[] tArr = t.toCharArray();
        
        Arrays.sort(sArr);
        Arrays.sort(tArr);
        
        return Arrays.equals(sArr, tArr);
        
    }
}

```
