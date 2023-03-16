# Implement queue with stacks

## Strategy

*

```java
class MyQueue {

    private int front;
    Stack<Integer> stack1 = new Stack();
    Stack<Integer> stack2 = new Stack();
    public MyQueue() {
    }
    
    public void push(int x) {
        if (stack1.isEmpty()) { // first element in empty queue     
            front = x;
        }
            
        while (!stack1.isEmpty()) { // invert main stack into secodary
            stack2.push(stack1.pop());
        }
        stack1.push(x); // add new emement
        while (!stack2.isEmpty()) { // reinvert secondary stack on top of new element
            stack1.push(stack2.pop());
        }
    }
    
    public int pop() {
        int res = stack1.pop(); // just regular pop
        
        if (!stack1.empty()) {
            front = stack1.peek(); // set front variable for peek
        }
        return  res;
        
    }
    
    public int peek() {
        return front; // simply return front
    }
    
    public boolean empty() {
        return stack1.isEmpty(); // same as stack meathod
    }
}

/**
 * Your MyQueue object will be instantiated and called as such:
 * MyQueue obj = new MyQueue();
 * obj.push(x);
 * int param_2 = obj.pop();
 * int param_3 = obj.peek();
 * boolean param_4 = obj.empty();
 */
```
