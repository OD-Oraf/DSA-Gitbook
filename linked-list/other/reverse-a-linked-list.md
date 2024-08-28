# Reverse a Linked List

## Strategy - Iterative

* Create a null ListNode to serve as new head
* Store the next node in temp variable
* Set next to previous ListNode
* Set previous node to same value as current
* Update current to next
* Go from
  * 1 -> 2 -> 3 -> NULL
  * NULL <- 1 <- 2 <- 3
  * Return prev with will be last eeml

### Time complexity

* Time: O(N) - Visit each node once
* Space: O(1) - Space constant with Linked-list





<pre class="language-java"><code class="lang-java">/**
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
<strong>        
</strong>        // Purpose of temp is to do iteration
        // set curr to temp once pointing is revesed
        while (curr != null) {
            ListNode temp = curr.next; //use to keep next from current for traverse
            curr.next = newHead; // set pointer
            newHead = curr; //set node value
            
            
            curr = temp;// continue traversal
        }
        return newHead;
    }
}
</code></pre>

### Strategy - Recursive

* Video Solution Link -  [https://www.youtube.com/watch?v=S92RuTtt9EE\&t=325s](https://www.youtube.com/watch?v=S92RuTtt9EE\&t=325s)

```java
public ListNode reverseList(ListNode head) {
    /* recursive solution */
    return reverseListInt(head, null);
}

private ListNode reverseListInt(ListNode head, ListNode newHead) {
    if (head == null)
        return newHead;
    ListNode next = head.next;
    head.next = newHead;
    return reverseListInt(next, head);
}
```
