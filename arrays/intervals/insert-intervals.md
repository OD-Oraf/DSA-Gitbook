# Insert Intervals

## Strategy - Insert via for loop

* Insert interval while preserving order based on interval start
* Compare intervals to figure out if there is no overlap
  * If no overlap, figure out which interval comes first
* Iterate through intervals and merge based on overlap
  * Overlap = true if min(endings) - max(startings) >= 0
  * New interval = {min(starting), max(ending)}

### Example

```java
/*
intervals = [[1,2],[3,5],[6,7],[8,10],[12,16]], newInterval = [4,8]

Step 1.1 - Insert interval(preserve order of interval start)
intervals = [[1,2],[3,5],[4,8],[6,7],[8,10],[12,16]]

Step 2.1 - Merge overlapping intervalsintervals
currInterval = (1,2), next = (3,5) -> no overlap
answer = [[1,2]]

Step 2.2
currInterval = (3,5), next = (4,8) -> overlap
currInterval = (3,8)

Step 2.3
currInterval = (3,8), next = (6,7) -> overlap
currInterval = (3,8)

Step 2.4
currInterval = (3,8), next = (8,10) -> overlap
currInterval = (3,10)

Step 2.5
currInterval = (3,10), next = (12,16) -> no overlap
answer = [[1,2],[3,10]]

Step 2.6
last index
answer = [[1,2],[3,10],[12,16]]
*/
```

```java
class Solution {
    public int[][] insert(int[][] intervals, int[] newInterval) {
        
        List<int[]> result = new ArrayList<>();
        
        // Iterate through all slots
        for(int[] interval : intervals)
        {
            
            // if newInterval before slot insert newInterval & update slot as new interval
            if(newInterval[1] < interval[0])
            {
                result.add(newInterval);
                newInterval = interval;// new interval represents the unmerged interval
            } 
            
            // if slot is lesser than new Interval insert slot
            else if(interval[1] < newInterval[0])
            {
                result.add(interval);
            } 
            
            // if above conditions fail its an overlap since possibility of new interval existing in left & right of slot is checked
            // update lowest of start & highest of end & not insert
            else {
                newInterval[0] = Math.min(newInterval[0],interval[0]);
                newInterval[1] = Math.max(newInterval[1],interval[1]);
            }
        }
        
        // insert the last newInterval -> possible that the interval is updated but not added to result
        result.add(newInterval);
        
        // convert to int[][] array
        return result.toArray(new int[result.size()][]);
    }
}
```

```java
class Solution {
    
    boolean doesIntervalsOverlap(int[] a, int[] b) {
       /* Size of overlap = min(ending) - max(starting)
        
            1------3
               2-----------------5

        */
        return Math.min(a[1], b[1]) - Math.max(a[0],b[0]) >= 0;
    }
        
    int[] mergeIntervals(int[] a, int[] b){// return merged interval
        int[] newInterval = {Math.min(a[0], b[0]), Math.max(a[1], b[1])};
        return newInterval;
    }
    

    int[][] insertInterval(int[][] intervals, int[] newInterval) {
        boolean isIntervalInserted = false;
        List<int[]> list = new ArrayList<>(Arrays.asList(intervals));
        //Insert interval and preserve interval start order
        for (int i = 0; i < intervals.length; i++) {
            if (newInterval[0] < intervals[i][0]) {
                list.add(i, newInterval);
                isIntervalInserted = true;
                break;
            }
        }
        /*
        If insert at end if starting is larger than aother other starting intervals
        */
        if (!isIntervalInserted) {
            list.add(newInterval);
        }

        return list.toArray(new int[list.size()][2]);
    }
    
    public int[][] insert(int[][] intervals, int[] newInterval) {
        intervals = insertInterval(intervals, newInterval);
        List<int[]> answer = new ArrayList<>();
        
        for (int i = 0; i < intervals.length; i++) {
            int[] currInterval = {intervals[i][0], intervals[i][1]};
            //Iterate and check for overlapping intervals
            while (
                i < intervals.length 
                && doesIntervalsOverlap(currInterval, intervals[i])
                ) {
                currInterval = mergeIntervals(currInterval, intervals[i]);
                i++;
            }
            // Decrement to ensure we don't skip the interval due to outer for-loop incrementing.
            i--;
            answer.add(currInterval);
        }
        
        return answer.toArray(new int[answer.size()][2]);
        
    }
}
```

##
