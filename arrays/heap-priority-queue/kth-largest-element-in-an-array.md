# Kth Largest Element in an Array

## Strategy - Min Heap (priority queue)

* Use a priority queue which basically sorts the array wih the smallest at the beginning of the list

```java
class Solution {
    public int findKthLargest(int[] nums, int k) {
        // Use priority queue as min heap
        PriorityQueue<Integer> heap = new PriorityQueue<>();
        for (int num : nums) {
            heap.add(num);
            if (heap.size() > k) {
                heap.poll();
            }
        }
        
        return heap.peek();
        
    }
}
```
