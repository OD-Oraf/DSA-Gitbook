# Non-Overlapping Intervals

### Strategy - Greedy

![](<../../.gitbook/assets/image (5).png>)

```java
class Solution {
    public int eraseOverlapIntervals(int[][] intervals) {
        int intervalsRemoved = 0; // keep count to be returned
        
        Arrays.sort(intervals, (a,b) -> Integer.compare(a[0], b[0])); // sort array
        
        int[] intervalFirst = intervals[0]; // interval for comparison
        
        for (int i = 1; i < intervals.length; i++) {
            if (firstIntervalWithinSecond(intervalFirst, intervals[i])) {
                // if there is overlap keep one that ends first, remove other
                intervalsRemoved++;
                
                if (intervalFirst[1] > intervals[i][1]) {
                    intervalFirst = intervals[i];
                }
            } else {
                intervalFirst = intervals[i];
            }
        }
        return intervalsRemoved;
    }
    
    public boolean firstIntervalWithinSecond(
        int[] intervalFirst,
        int[] intervalSecond
    ) {
        // Return true on overlap between end of first and begin of second
        return intervalFirst[1] > intervalSecond[0]; 
    }
}
```
