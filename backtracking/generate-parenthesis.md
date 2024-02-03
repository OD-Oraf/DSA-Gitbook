# Generate Parenthesis

### Strategy -&#x20;

* 3 Keys
  * Our choice
    * Place a "(" or ")"
  * Our Constraints
    * We cannot close a parenthesis until we open.
    * Count of left opens matters
  * Our Goal&#x20;
    * n\*2 placements - n = 3 -> 3 open 3 close

### Summary

* Only add open parenthesis if open < n
* Only add closing if close < open
* Valid if and only if open==closed=n

### Time/Space Complexity

```java
/* 
n=3
                              Open <> Close
                                  " "
                                   |
                                  "("
                      /                           \   
                   "(("                           "()"
                 /        \                      /     \
                "((("   "(()"                 "()("    ""
                        /  \                   /  \
                           "((()"         "()(("  "()()"
                               \                    /\
                               "((())"         "()()("
                                   \
                                   "((()))"
*/


```

```java
class Solution {
    public List<String> generateParenthesis(int n) {
        List<String> ans = new ArrayList(); // Array of string solutions
        backtrack(ans, "", 0, 0, n);
        return ans;
        
    }
    
    public void backtrack(List<String> ans, String currString, int open, int close, int max) {
        if (currString.length() == max * 2) { // push current string to answer once complete
            ans.add(currString);
            return;
        }
        
        if (open < max) { // open parenthesis less than max
            backtrack(ans, currString + "(", open + 1, close, max);
        }
        
        if (close < open) {
            backtrack(ans, currString + ")", open, close + 1, max);
        }
    }
}
```

```java
// recursion explained

n = 2
backtrack(ans,currString,open,close,max) -> backtrack([],"",0,0,2)

open(0) < max(2) -> true 
backtrack([],"(",1,0,2)

    open(1) < max(2) -> true
    backtrack([],"((",2,0,2)
    
        open(2) < max(2) -> false
        close(0) < open(2) -> true
        backtrack([],"(()",2,1,2)
        
            close(1) < open(2) -> true
            backtrack([],"(())",2,2,2)
            
                currString.len(4) == max(2)*2 > true
                ans = ["(())"]
         
                
        
        
```
