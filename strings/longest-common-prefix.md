# Longest Common Prefix

## Strategy

* Set first word as the prefix and iterate through list. Shave down preset until its matching current word. Return the shaved down prefix
* Important methods
  * indexOf()
  * substring()

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
