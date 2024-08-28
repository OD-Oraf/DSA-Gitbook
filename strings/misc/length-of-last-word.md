# Length of Last Word

## Strategy - Count words from the end

### Time/Space

* Time -> O(n)&#x20;
  * Worst case we have to scan the entire array -> "s            "
* Time -> O(1)
  * No extra space used&#x20;

```java
class Solution {
    public int lengthOfLastWord(String s) {
        
        int i = s.length() - 1;
        while (i >=0 && s.charAt(i) == ' ') {
            i--;
        }
        
        int len = 0;
        while(i >= 0 && s.charAt(i) != ' ') {
            i--;
            len++;
        }
        return len;
        
    }
}
```
