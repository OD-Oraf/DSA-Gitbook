# Reverse a linked list

## Strategy (Iterative)

* Create a null ListNode to serve as new head
* Store the next node in temp variable
* Set next to previous ListNode
* Set previous node to same value as current
* Update current to next

### Time complexity

* Time: O(N) - Visit each node once
* Space: O(1) - Space constant with LinkedList

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
    public ListNode reverseList(ListNode head) {
        // Reverse Linked listy
        
        ListNode newHead = null; 
        ListNode curr = head; 
        
        // Purpose of temp is to do iteration
        // set curr to temp once pointing is revesed
        while (curr != null) {
            ListNode temp = curr.next;
            curr.next = newHead;
            newHead = curr; 
            
            
            curr = temp;
        }
        return newHead;
    }
}
```
