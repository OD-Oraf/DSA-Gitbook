# Backspace string compare

## Strategy - Stack

* Approach 1&#x20;
  * Use stack to remove characters deleted by the backspace

### Important!!

* .equals() to evaluate stirng equivalency
* String.valueOf(stack) - convert stack to string

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


//Alternate
class Solution {
    public boolean backspaceCompare(String s, String t) {
        
        String sBackspaced = removeBackspace(s);
        String tBackspaced = removeBackspace(t);
        
        return sBackspaced.equals(tBackspaced);
        
    }
        
    
    
    public String removeBackspace(String str) {
        Stack<Character> stack = new Stack();
        
        for (char c : str.toCharArray()) {
            if (c == '#' && !stack.isEmpty()) {
                stack.pop();
            }
            if (c != '#') {
                stack.push(c);
            }
        }
        
        return stack.toString();
    }
}

```

## Strategy - Two Pointers

```java
class Solution {
    public boolean backspaceCompare(String S, String T) {
        int i = S.length() - 1, j = T.length() - 1;
        int skipS = 0, skipT = 0;

        while (i >= 0 || j >= 0) { // While there may be chars in build(S) or build (T)
            while (i >= 0) { // Find position of next possible char in build(S)
                if (S.charAt(i) == '#') {skipS++; i--;}
                else if (skipS > 0) {skipS--; i--;}
                else break;
            }
            while (j >= 0) { // Find position of next possible char in build(T)
                if (T.charAt(j) == '#') {skipT++; j--;}
                else if (skipT > 0) {skipT--; j--;}
                else break;
            }
            // If two actual characters are different
            if (i >= 0 && j >= 0 && S.charAt(i) != T.charAt(j))
                return false;
            // If expecting to compare char vs nothing
            if ((i >= 0) != (j >= 0))
                return false;
            i--; j--;
        }
        return true;
    }
}
```
