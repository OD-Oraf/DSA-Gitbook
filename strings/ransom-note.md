# Ransom Note

## Strategy(One Hash Map)

* Keep character count in hashmap and check if ransomNote passes validation against hashmap

## Time Complexity

* Time: O(magazine) \~ O(M)
  * Longest this algorithm with go for is length of the magazine. NOTE!! **Magazine must be longer than randomNote** otherwise there aren't enough letters
* Space: O(1)
  * Access for hashmap is O(1) as well as string is O(1)

```java
class Solution {
    public boolean canConstruct(String ransomNote, String magazine) {
        // Put magazin into hashmap with character count
        // index through ransom note and see if its existing in hashmap
        // if not existing return false
        // return true if loop finishes
        
        // Not enough letters for ransom note
        if (magazine.length() < ransomNote.length()) {
            return false;
        }
        
        // Create chracter count map for magazine
        HashMap<Character, Integer> map = new HashMap();
        for (int i = 0; i < magazine.length(); i++) {
            char c = magazine.charAt(i);
            map.put(c, map.getOrDefault(c, 0) + 1);
        }
        
        for (int i = 0; i < ransomNote.length(); i++) {
            char c = ransomNote.charAt(i);
            if (!map.containsKey(c)) {
                return false;
            } else {
                map.put(c, map.get(c) - 1);
                if (map.get(c) == 0) {
                    map.remove(c);
                }
            }
        }
        
        return true;
        
    }
}
```
