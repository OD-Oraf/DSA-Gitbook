# Baseball Game

{% embed url="https://leetcode.com/problems/baseball-game/" %}

```java
class Solution {
    public int calPoints(String[] operations) {
        Stack<Integer> stack = new Stack<>();
        for (String c : operations) {
            if (c.equals("+")) {
                // Add previous 2 records
                int top = stack.pop();
                int newTop = top + stack.peek();
                stack.push(top);
                stack.push(newTop);
            } else if (c.equals("D")) {
                stack.push(stack.peek() * 2);
            } else if (c.equals("C")) {
                stack.pop();
            } else {
                stack.push(Integer.valueOf(c));
            }
        }
        
        int res = 0;
        for (int i : stack) {
            res += i;
        }

        return res;
        
    }
}
```
