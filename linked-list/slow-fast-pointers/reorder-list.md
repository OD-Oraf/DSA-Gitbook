---
description: https://leetcode.com/problems/reorder-list/
---

# Reorder List

## Strategy - Reverse Second Part and Merge

* This problem is a combination of three problems
  * Middle of a linked List
  * Reverse Linked List&#x20;
  * Merge Two Sorted Lists

### Subproblem - Middle of Linked List

```java
 // Find midpoint of list
        ListNode slow = head;
        ListNode fast = head;
        
        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next; 
        }
        
        ListNode mid = slow;
```

### Subproblem - Reverse Linked List

```java
// Reverse Linked list
        ListNode prev = null;
        ListNode curr = mid;
        
        while (curr != null) {
            ListNode temp = curr.next;
            curr.next = prev;
            prev = curr;
            
            curr = temp;
        }
```

### Subproblem - Merge sorted linked lists

```java
// Merge the sorted linked lists
        ListNode first = head; // First list
        ListNode second = prev; // head of reversed linked list 
        while (second.next != null) {
            ListNode temp = first.next; // Use to get next element of first
            first.next = second;
            first = temp; // after pointing, update first to next iteration
            
            temp = second.next; // use to get next element of second
            second.next = first;
            second = temp; // after pointing, update second to next iteration
        } 
```

### Full Solution

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
    public void reorderList(ListNode head) {
        /*
            Find middle of list - Use fast slow pointer
            Reverse Second partition
            Merge lists so that each node alternates between the first and second partitions
        */
        
        // Find midpoint of list
        ListNode slow = head;
        ListNode fast = head;
        
        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next; 
        }
        
        ListNode mid = slow;
        
        // Reverse Linked list
        ListNode prev = null;
        ListNode curr = mid;
        
        while (curr != null) {
            ListNode temp = curr.next;
            curr.next = prev;
            prev = curr;
            
            curr = temp;
        }
        
        // Merge the sorted linked lists
        ListNode first = head; // First list
        ListNode second = prev; // head of reversed linked list 
        while (second.next != null) {
            ListNode temp = first.next; // Use to get next element of first
            first.next = second;
            first = temp; // after pointing, update first to next iteration
            
            temp = second.next; // use to get next element of second
            second.next = first;
            second = temp; // after pointing, update second to next iteration
        }
        
        
    }
}
```
