# Merge Two Sorted Lists

## Strategy&#x20;

* Use slow/fast pointer
  * slow = slow.next
  * fast = fast.next.next
* stop when fast pointer or fast.next reaches the end
* If there is a cycle the fast pointer will catch up to the slow pointer.

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
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        
        if (list1 == null) {
            return list2;
        }
        if (list2 == null) {
            return list1;
        }
        
        if (list1.val <= list2.val) {
            list1.next = mergeTwoLists(list1.next, list2);
            return list1;
        } else {
            list2.next = mergeTwoLists(list1, list2.next);
            return list2;
        }
        
    }
}
```

