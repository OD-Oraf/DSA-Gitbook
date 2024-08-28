# Last Stone Weight

```java
class Solution {
    public int lastStoneWeight(int[] stones) {
        // get two largest numbers take absolute differecne and enter back in array of 1
        if (stones.length == 1) {
            return 1;
        }
        
        PriorityQueue<Integer> maxHeap = new PriorityQueue<>(Comparator.reverseOrder());
        for (int stone : stones) {
            maxHeap.add(stone);
        }
        
        while (maxHeap.size() > 1) {
            int firstStone = maxHeap.poll();
            int secondStone = maxHeap.poll();
            int newStone = firstStone - secondStone;
            if (newStone > 0) {
                maxHeap.add(newStone);
            }
        }
        
        
        return maxHeap.isEmpty() ? 0 : maxHeap.peek();
        
    }
}
```

