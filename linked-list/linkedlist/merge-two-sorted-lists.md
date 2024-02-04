# Merge Two Sorted Lists

## Strategy - Recursion&#x20;

*

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

### Strategy - Iterative

* Use dummy head as beginning of list&#x20;
  * Cannot be null **(Find out why)**
* Update pointers based on value
* When one linked list returns null just point next to the non null node

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
        ListNode dummy = new ListNode(-1);
        
        ListNode prev = dummy;
        ListNode curr1 = list1;
        ListNode curr2 = list2;
        
        while (curr1 != null && curr2 != null) {
            if (curr1.val <= curr2.val) {
                prev.next = curr1;
                curr1 = curr1.next;
                
            } else {
                prev.next = curr2;
                curr2 = curr2.next;
            }
            
            prev = prev.next;
        }
        
        prev.next = curr1 == null ? curr2 : curr1; 
        
        return dummy.next;
        
        
    }
    

}
```
