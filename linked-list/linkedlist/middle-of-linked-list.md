# Middle of Linked List

## Slow/fast pointers approach

Use slow fast pointer.

When fast pointer reaches end slow pointer will be in middle becasue slow is moving half as fast as fast pointer

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode middleNode(ListNode head) {
        if (head == null) {
            return head;
        }
        ListNode slow = head;
        ListNode fast = head;
        
        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }
        
        return slow;
        
    }
}
```

### Linked List to array solution

* LinkedList2ArraySolution: Convert linked list to array and return midpoint. Initialize array with length 100 as linked list can be 100 nodes long

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode middleNode(ListNode head) {
        
        ListNode[] llToArray = new ListNode[100];
        ListNode curr = head;
        int iterator = 0;
        while (curr != null) {
            llToArray[iterator] = curr;
            curr = curr.next;
            iterator++;
        }
        
        return llToArray[iterator / 2];
        
    }
}
```
