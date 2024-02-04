# Remove Nth Node From End of List

## Strategy - Left and Right Pointers

* Create dummy head to get spacing between left and right pointers
* Traverse both until right hits end of array
* Set left.next to left.next.next
*

    <figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

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
    public ListNode removeNthFromEnd(ListNode head, int n) {
        
        ListNode prev = new ListNode(-1);
        prev.next = head;
        
        ListNode left = prev;
        ListNode right = head;
        
        int iterator = 0;
        
        while (iterator < n){
            right = right.next;
            iterator++;
        }
        while (right != null) {
            right = right.next;
            left = left.next;          
        }
        
        left.next = left.next.next;
        // Return nth node from reversed list
        
        
        return prev.next;
        
        
    }
}
```
