# Merge Intervals

## Strategy

*

```java
package com.company.arrays;

import java.util.*;

public class MergeIntervals {

    public static int[][] mergeIntervals(int[][] intervals) {
        /* Steps:
            Sort intervals by starting value
            Push first interval into stack

            For each interval
                if current interval does not overlap
                    Push to stack
                if current intervals overlaps with stack top and
                ending is greater than stack top, update stack top with ending tim oe current interval

            Stack of merged intervals
        */
        if (intervals.length <= 1) {
            return intervals;
        }

        Arrays.sort(intervals, (a, b) -> Integer.compare(a[0], b[0]));
        LinkedList<int[]> merged = new LinkedList<>();


        for (int i = 0; i < intervals.length; i++) {
            // Overlap
            if (merged.isEmpty() || merged.getLast()[1] < intervals[i][0]) {
                merged.add(intervals[i]);
            } else {
                merged.getLast()[1] = Math.max(merged.getLast()[1], intervals[i][1]);
            }
        }
        return merged.toArray(new int[merged.size()][]);

    }

//    static void printArray(int[][] intervals) {
//        for (int[] interval: intervals) {
//            System.out.println(Arrays.toString(interval));
//        }
//    }
    public static void main(String[] args) {

        int[][] intervals = {
                {1,7},
                {2,6},
                {8,10},
                {15,18}
        };

//        printArray(mergeIntervals(intervals));
        int [][] merged = mergeIntervals(intervals);
        for (int[] interval : merged) {
            System.out.println(Arrays.toString(interval));

        }
//        printArray(intervals);


    }
}

```



