# Design Linked List

Link: [https://leetcode.com/problems/design-linked-list/](https://leetcode.com/problems/design-linked-list/)

```java
public class ListNode {
    int val;
    ListNode next;
    
    ListNode (int x) {
        val = x;
    }
}

class MyLinkedList {
    
    int size; 
    ListNode head;
    
    public MyLinkedList() {
        size = 0;
        head = new ListNode(0);// sentinel(dummy) head
    }
    
    public int get(int index) {
        if (index < 0 || index >= size) {//invalid index
            return -1;
        }
        ListNode curr = head;
        for (int i = 0; i < index + 1; i++) {
            curr = curr.next;
        }
        return curr.val;
        
    }
    
    public void addAtHead(int val) {
        addAtIndex(0, val);
    }
    
    public void addAtTail(int val) {
        addAtIndex(size, val);
    }
    
    public void addAtIndex(int index, int val) {
        if (index > size) {//invalid index
            return;
        }
        if (index < 0) {
            index = 0;
        }
        size++;
        
        ListNode prev = head;
        for (int i = 0; i < index; i++) {
            prev = prev.next;
        }
        ListNode toAdd = new ListNode(val);
        
        toAdd.next = prev.next;
        prev.next = toAdd;
    }
    
    public void deleteAtIndex(int index) {
        if (index < 0 || index >= size) {//invalid index
            return;
        }
        size--;
        
        ListNode prev = head;
        for (int i = 0; i < index; i++) {
            prev = prev.next;
        }
        
        prev.next = prev.next.next;
    }
}

/**
 * Your MyLinkedList object will be instantiated and called as such:
 * MyLinkedList obj = new MyLinkedList();
 * int param_1 = obj.get(index);
 * obj.addAtHead(val);
 * obj.addAtTail(val);
 * obj.addAtIndex(index,val);
 * obj.deleteAtIndex(index);
 */
```
