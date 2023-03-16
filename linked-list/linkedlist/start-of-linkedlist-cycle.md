# Start of LinkedList Cycle

## Strategy&#x20;

* Find where slow and fast pointer meets
* Use that node to find length of cycle
* Use length of cycle to find start3



```java
class ListNode {
  int value = 0;
  ListNode next;

  ListNode(int value) {
    this.value = value;
  }
}

class LinkedListCycleStart {

  public static ListNode findCycleStart(ListNode head) {
    // TODO: Write your code here
    /** STEPS
      1. Find where slow and fast pointer meets
      2. Use that  Node to find length of cycle
      3. Use length of cycle to find the start
    **/
    
    // null check
    if (head == null) {
      return head;
    }

    ListNode slow = head;
    ListNode fast = head;
    int cycleLength = 0;
    while (fast != null && fast.next != null) {
      slow = slow.next;
      fast = fast.next.next;
      if (slow == fast) { 
        cycleLength = calculateCycleLength(slow);
        break;
      }
    }
    return findStart(head, cycleLength);
  }

  public static int calculateCycleLength(ListNode slow) {
    ListNode current = slow;
    int cycleLength = 0;
    do {
      cycleLength++;
      current = current.next;
    } while (current != slow);

    return cycleLength;
  }

  public static ListNode findStart(ListNode head, int cycleLength) {
    ListNode p1 = head;
    ListNode p2 = head;

    while (cycleLength > 0) {
      p2 = p2.next;
      cycleLength--;
    }

    while (p1 != p2) {
      p1 = p1.next;
      p2 = p2.next;
    }

    return p1;

  }

  public static void main(String[] args) {
    ListNode head = new ListNode(1);
    head.next = new ListNode(2);
    head.next.next = new ListNode(3);
    head.next.next.next = new ListNode(4);
    head.next.next.next.next = new ListNode(5);
    head.next.next.next.next.next = new ListNode(6);

    head.next.next.next.next.next.next = head.next.next;
    System.out.println("LinkedList cycle start: " + LinkedListCycleStart.findCycleStart(head).value);

    head.next.next.next.next.next.next = head.next.next.next;
    System.out.println("LinkedList cycle start: " + LinkedListCycleStart.findCycleStart(head).value);

    head.next.next.next.next.next.next = head;
    System.out.println("LinkedList cycle start: " + LinkedListCycleStart.findCycleStart(head).value);
  }
}
```
