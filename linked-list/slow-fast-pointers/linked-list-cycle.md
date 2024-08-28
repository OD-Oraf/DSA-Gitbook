# Linked List Cycle

## Strategy - Slow fast pointers&#x20;

* Use slow/fast pointer
  * slow = slow.next
  * fast = fast.next.next
* stop when fast pointer or fast.next evaluates as null
  * **Important!** Why do we need to check fast.next in while condition?
    * 1 -> 2 -> 3 -> null
    * if fast = 3 then  fast.next.next == null pointer exception because null.next &#x20;
      * We check fast.next so we avoid null pointer&#x20;
* If there is a cycle the fast pointer will catch up to the slow pointer.

```java
/**
 * Definition for singly-linked list.
 * class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public boolean hasCycle(ListNode head) {
        // Use fast as slow pointers to catch cyclce
        // Make sure to check fast.next to detect null from last element in list
            
        if (head == null) {
            return false;
        }
        
        ListNode slow = head;
        ListNode fast = head;
        
        while (fast != null && fast.next != null) {
            slow = slow.next; 
            fast = fast.next.next;
            
            if (slow == fast) {
                return true;
            }
            
        }
        
        return false;
        
    }
}
```

### Time complexity

* Time: No-cycle - O(n) - Number of nodes in the linked list
  * Cycle -> O(N + K)
* Space -> O(1) since only using slow and fast pointers

### Alternate solution

```java
/**
 * Definition for singly-linked list.
 * class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 **/
public class Solution {
    public boolean hasCycle(ListNode head) {
        if (head == null || head.next == null) {
            return false;
        }
        // Slow and fast pointers
        ListNode slow = head;
        ListNode fast = head.next;

        while (slow != fast) {
            if (fast == null || fast.next == null) {
                return false;
            }
            
            slow = slow.next;
            fast = fast.next.next;
        }
        
        return true;
        
    }
}


```

## Strategy - HashMap

* Use a hashmap to keep track of visited nodes

```java
public class Solution {
    public boolean hasCycle(ListNode head) {
        Set<ListNode> nodesSeen = new HashSet<>();
        ListNode current = head;
        while (current != null) {
            if (nodesSeen.contains(current)) {
                return true;
            }
            nodesSeen.add(current);
            current = current.next;
        }
        return false;
    }
}
```
