# Kth Largest Element in a Stream

## Strategy - Priority Queue

* Minheap
  * add/pop -> O(logn)&#x20;
  * get min value -> O(1)

### Time/Space

* Time -> O(N\*log(N) + M\*log(k))
* Space -> O(N)

```java
class KthLargest {
    private PriorityQueue<Integer> heap;
    private int k;

    public KthLargest(int k, int[] nums) {
        heap = new PriorityQueue<>();
        this.k = k;
        for (int num : nums) {
            add(num);
        }
        
    }
    
    public int add(int val) {
        heap.add(val);
        if (heap.size() > k) {
            heap.poll();
        }
        return heap.peek();
    }
}

/**
 * Your KthLargest object will be instantiated and called as such:
 * KthLargest obj = new KthLargest(k, nums);
 * int param_1 = obj.add(val);
 */
```
