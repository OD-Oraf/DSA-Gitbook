# Design Browser History

Link: [https://leetcode.com/problems/design-browser-history/](https://leetcode.com/problems/design-browser-history/)

```java
public class DLLNode {
    DLLNode prev;
    DLLNode next;
    String data;
    
    DLLNode(String url) {
        data = url;
        prev = null;
        next = null;
    }
}

class BrowserHistory {
    
    DLLNode current;
    DLLNode head;
    
    public BrowserHistory(String homepage) {
        head = new DLLNode(homepage);
        current = head;
    }
    
    public void visit(String url) {
        DLLNode newNode = new DLLNode(url);
        current.next = newNode;
        newNode.prev = current; 
        
        current = newNode;
    }
    
    public String back(int steps) {
        while (steps > 0 && current.prev != null) {
            current = current.prev;
            steps--;
        }
        return current.data;
    }
    
    public String forward(int steps) {
        while (steps > 0 && current.next != null) {
            current = current.next;
            steps--;
        }
        return current.data;
    }
}

/**
 * Your BrowserHistory object will be instantiated and called as such:
 * BrowserHistory obj = new BrowserHistory(homepage);
 * obj.visit(url);
 * String param_2 = obj.back(steps);
 * String param_3 = obj.forward(steps);
 */
```
