# Backspace string compare

## Strategy

* Approach 1&#x20;
  * Use stack to remove characters deleted by the backspace

```java
class Solution {
    public boolean backspaceCompare(String s, String t) {
        
        return buildString(s).equals(buildString(t));
        
    }
    
    public String buildString(String s) {
        Stack<Character> stack = new Stack<>();
        for (char c : s.toCharArray()) {
            
            if (c != '#') {
                stack.push(c);
            } else if (!stack.isEmpty()) {
                stack.pop();
            }
        }
        
        return String.valueOf(stack);
    }
}
```
