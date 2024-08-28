# Valid Parenthesis String (Greedy)



```java
class Solution {
    public boolean checkValidString(String s) {
        int openMin = 0, openMax = 0; // open parentheses count in range [openMin, openMax]
        for (char c : s.toCharArray()) {
            if (c == '(') { // both increase because they are definety open
                openMax++;
                openMin++;
            } else if (c == ')') { // both decrease because they are definetly closed
                openMax--;
                openMin--;
            } else if (c == '*') {
                openMax++; // if `*` become `(` then openCount++
                openMin--; // if `*` become `)` then openCount--
                // if `*` become `` then nothing happens
                // So openCount will be in new range [cmin-1, cmax+1]
            }
            if (openMax < 0) return false; // Currently, don't have enough open parentheses to match close parentheses-> Invalid
                                        // For example: ())(
            openMin = Math.max(openMin, 0);   // If openMin is less than 0 disregard as a valid path
        }
        return openMin == 0; // Return true if can found `openCount == 0` in range [cmin, cmax]
    }
}
```
