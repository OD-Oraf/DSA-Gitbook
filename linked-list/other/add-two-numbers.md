# Add Two Numbers

[https://leetcode.com/problems/add-two-numbers/submissions/](https://leetcode.com/problems/add-two-numbers/submissions/)

## Strategy

* The main idea is to extract the carry and apply to the next node
* To carry a digit, take the tens place, x / 10
* For the digit to be used in the answer, take the ones place, x % 10
* Remember to update the nodes as needed

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
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode prev = new ListNode(-1);
        ListNode curr = prev;
        int carry = 0;
        
        while (l1 != null || l2 != null || carry != 0){
            int x = (l1 == null) ? 0 : l1.val;
            int y = (l2 == null) ? 0 : l2.val;
            int sum = x + y + carry;
            carry = sum / 10;//Take tens place of sum for carry
            curr.next = new ListNode(sum % 10);//Take ones place for answer
            curr = curr.next;//update current node
            if (l1 != null) {
                l1 = l1.next;
            }
            if (l2 != null) {
                l2 = l2.next;
            }
        }
        
        return prev.next;
        
        
    }
}
```
