# Is subsequnce

## Strategy - Two Pointer

* Use two pointers to index through s and t
  * When they are equal update both pointers,
  * If not only update t to skip non-matching characters
* Return if s pointer makes it to end of array

```java
class Solution {
    public boolean isSubsequence(String s, String t) {
        if (s.length() == 0) {
            return true;
        }
        
        int sPointer = 0;
        int sLen = s.length();
        
        int tPointer = 0;
        int tLen = t.length();
        
        
        
        while (sPointer < sLen && tPointer < tLen) {
            if (s.charAt(sPointer) == t.charAt(tPointer)) {
                sPointer++;
                tPointer++;
            } else {
                tPointer++;
            }
        }
        
        return sPointer == sLen;
        
    }
}
```
