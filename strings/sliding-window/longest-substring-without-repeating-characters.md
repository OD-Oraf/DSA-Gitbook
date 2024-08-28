# Longest Substring without repeating Characters

## Strategy

* Sliding window pattern
* Whenever we have duplicate character in window remove it by updating **map count** and **left pointer**
  * **DO NOT FORGET LEFT POINTER!!!!!!**
* Remember&#x20;
  * **i - left + 1** to account for index starting at 0
  * ```java
    map.getOrDefault()
    ```

## Sliding Window

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

## Optimized Sliding window

### Notes

#### Why do we need Math.max(left, map.get(c))?

Using the example "abba"&#x20;

We run into the scenario where we hit one duplicate"b" at index 2 and update the left pointer to 2 since the original "b" is at index 1.

On the next iteration we hit "a" whose original is actually now outside the window due to the earlier duplicate. If we were to update left as left = map.get(c) + 1, it would update the pointer to 1 which would re-introduce the duplicated "b". Taking the max prevents the left pointer from going "backwards" and re-introducing duplicates that were excluded from the window &#x20;

IN SORT: Use a hashmap to track the index of char c's last index. Update left to this if the duplicate is found(existing in hashmap already) and update the last index

```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        HashMap <Character, Integer> map = new HashMap();
        int left = 0;
        int maxLen = 0;
        
        for (int i = 0; i< s.length(); i++) {
            char c = s.charAt(i);
            if (map.containsKey(c)) {// if char is already existing
                left = Math.max(left, map.get(c));// set left to the index of char's last instance
            }
            map.put(c,i + 1);// update the index of char's last instance
            maxLen = Math.max(maxLen, i - left + 1);// calculate sum
        }
        
        return maxLen;
        
    }
}
```

```java
// Some code

"abba"

if (map.containsKey(c)){
    left = map.get(c) + 1 
}

"a" i = 0, left = 0, map:{"a":0},maxLen = 1;

"b" i = 1, left = 0, map:{"a":0,"b":1}, maxLen = 2;

"b" i = 2, left = 2, map:{"a":0,"b":2}, maxLen = 1;

"a" i = 3, left = 1, map:{"a":3,"b":2}, maxLen = 3;//incorrect
```
