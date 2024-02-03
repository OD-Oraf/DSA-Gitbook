---
description: \
---

# Linked List

## Singly linked list

Made up of ListNodes

Contains value and pointer to next ListNode

Does not have to be contiguous in memory like arrays

### Operations

<table><thead><tr><th width="242.33333333333331">Operation</th><th>Time Complexity </th><th>Notes</th></tr></thead><tbody><tr><td>Access</td><td>O(n)</td><td></td></tr><tr><td>Search </td><td>O(n)</td><td>To get to n^th element, need to traverse n nodes</td></tr><tr><td>Insertion</td><td>O(1)</td><td>O(1) assuming reference to desired position</td></tr><tr><td>Deletion</td><td>O(1)</td><td></td></tr></tbody></table>

## Doubly Linked List

Two pointers for prev and next nodes. \\

Can be used to implement stack but less common&#x20;

### Operations

<table><thead><tr><th width="242.33333333333331">Operation</th><th>BIG-O Array</th><th>BIG-O LinkedList</th></tr></thead><tbody><tr><td>Access i^th element</td><td>O(1)</td><td>O(n)</td></tr><tr><td>Insert/remove end</td><td>O(1)</td><td>O(1)</td></tr><tr><td>Insert/remove middle</td><td>O(n)</td><td>O(1)</td></tr><tr><td>Deletion</td><td>O(1)</td><td></td></tr></tbody></table>
