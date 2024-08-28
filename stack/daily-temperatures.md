# Daily Temperatures

## Strategy - Monotonic Stack

* Monotonic decreasing stack -> Stack with strictly increasing or decreasing values
  * Good for comparing size of numeric elements with order being relevant
* To maintain stack&#x20;
  * Store indices of temperatures
  * If current day is same or colder than the top of the stack, push to stack
  * When we find a warmer day, the difference is the current index - top of stack
    * As long as current is greater than the top of the stack, we get the differences until the current element is smaller

### Algorithm -

* Init ans with same length as temperatures and set all values to 0&#x20;
* Init stack
* Iterate temperatures
  * If stack is not empty, there is a previous day that we havent found a warmer day for
  * While current temp os warmer than the previous day(top of stack)
    * ans\[prevDay] = currDay(top of stack)
  * push current indexz currDay onto stack
  * return answer

### Time/Space Complexity

* Time -> each element will be pushed and popped from the stack as most 2n times -> O(n)
* Space -> O(n) at most n for each element if the temperatures never get warmer

```java
class Solution {
    public int[] dailyTemperatures(int[] temperatures) {
        
        int[] ans = new int[temperatures.length];
        for (int i : ans) {
            ans[i] = 0;
        }
        Stack<Integer> stack = new Stack();
        stack.push(0);
        
        for (int i = 1; i < temperatures.length; i++) {
            int currTemp = temperatures[i];
            while (!stack.isEmpty() && currTemp > temperatures[stack.peek()]) {
                int prevDay = stack.pop();
                ans[prevDay] = i - prevDay;
            }
            stack.push(i);
        }
        
        return ans;
        
    }
}
```
