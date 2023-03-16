# Valid Parenthesis

The main condition to solve for is is the current characters is an opening or closing bracket. Handle closing and opening brackets separately

```java
class Solution {
    public boolean isValid(String s) {
        HashMap<Character, Character> map = new HashMap();
        Stack<Character> stack = new Stack(); 
        map.put(')', '(');
        map.put('}', '{');
        map.put(']', '[');
        
        for (int i = 0; i < s.length(); i++) {
            char c = s.charAt(i);
            
            if (map.containsKey(c)) {
                if (stack.isEmpty()) {
                    return false; // no matching bracket
                }
                if (stack.peek() == map.get(c)) {
                    stack.pop(); // if matching, pop from stack
                } else {
                    return false;
                }
            }
            
            if (!map.containsKey(c)) {
                stack.push(c); // if not yet in stack, push
            }  
            
        }
        return stack.isEmpty();                
    }
        
        
}

```

