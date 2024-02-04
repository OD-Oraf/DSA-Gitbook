# Longest Common Prefix

## Strategy - Horizontal Scan using prefix

* Set first word as the prefix and iterate through list. Shave down preset until its matching current word. Return the shaved down prefix
* Important methods
  * indexOf()
    * Returns 0 if valid substring
    * returns -1 if invalid substring
  * substring()

### Time Complexity-

* Time
  * O(S) - sum of all characters in all strings
  * In the worst case, all n strings are the same
    * The prefix is compared with all characters in all the other strings with S comparisons which is the sum of all characters in all arrays
* Space&#x20;
  * O(1)

```java
class Solution {
    public String longestCommonPrefix(String[] strs) {
        // set first word as the prefix and interate through list
        // while loop - shave down word until matching (common prefix)
        // return that prefix
        
        if (strs.length == 0) {
            return "";
        }
        
        String prefix = strs[0];
        for (int i = 1; i < strs.length; i++) {
            while (strs[i].indexOf(prefix)!= 0 && prefix.length() > 0) {
                prefix = prefix.substring(0, prefix.length() - 1);
            }
        }
        return prefix; 
        
    }
}
```

## Strategy - Vertical Scan&#x20;

* The idea is that you go though each word comparing one letter at a time
  * The termination condition for the nested for loop is if the current character is not matching with another in the same column or if the index of that character exceeds the length(out of bounds) for another word(essentially is index of outer loop is equal to length)
  * If for loops never terminate then we can return the entire first word&#x20;
* Similar time complexity  to Horizontal scan strategy

```java
class Solution {
    public String longestCommonPrefix(String[] strs) {
        if (strs == null || strs.length == 0) return "";
        for (int i = 0; i < strs[0].length() ; i++){// i - iterator for each letter(column)
            char c = strs[0].charAt(i);
            for (int j = 1; j < strs.length; j ++) {//j- iterator for each word in strs
                if (i == strs[j].length() || strs[j].charAt(i) != c)
                    return strs[0].substring(0, i);             
            }
        }
        return strs[0];
    }
}
```
