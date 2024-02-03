# Valid Parenthesis

### Strategy: HashMap, Stack -&#x20;

1. Create mapping for parenthesis
2. Create stack to keep track of last unmached parenthesis
3. For each character
   1. If open -> push to stack
   2. If closed -> check that stack is empty
      1. If True -> return false because incomplete
      2. If False ->  check that top of stack if mathing
         1. True -> pop top
         2. False -> return false, non matching bracket

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

### HashMap / Stack 2 -

```java
class Solution {
    public boolean isValid(String s) {
        // Use stack to get matching parenthesis
        Stack <Character> stack = new Stack();
        HashMap<Character, Character> map = new HashMap(); 
        map.put('}','{');
        map.put(']','[');
        map.put(')','(');
        
        for (char c : s.toCharArray()) {
            if (!map.containsKey(c)) { // opening bracket
                stack.push(c);
                continue;
            }
            
            
            if (map.containsKey(c)) { // closing bracket
                if (stack.isEmpty()) {
                    return false;
                }
                if (stack.peek() == map.get(c)) { // Closing bracket, stack.peek() match
                    stack.pop();
                } else {
                    return false;
                }
            }
        }
        
        return stack.isEmpty();
        
    }
}\
```
