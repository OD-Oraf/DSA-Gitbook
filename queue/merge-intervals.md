---
description: https://leetcode.com/problems/merge-intervals/
---

# Merge Intervals

## Strategy - Sort and Linked List

* Sort array
  * Arrays.sort(intervals), (a,b) -> Integer.compare(a\[0], b\[0]));
* Store elements in linked list as it has getLast() method to retrieve most recent element which is used to build the array of merged elements

### Example

Intervals = \[\[1,3], \[2,6], \[8,10], \[15,18]]

* Iteration 1&#x20;
  * Executed before loop
  * \[\[1,3]] - Push first interval to merged
* Iteration 2
  * getLast = \[1,3], current  = \[2,6] -> merge condition and take larger ending
  * merged = \[ \[1,6] ]
* Iteration 3
  * getLast = \[1,6], current = \[8,10] -> no overlap
  * merged = \[\[1,6], \[8,10]]
* Iteration 4
  * getLast = \[8,10], current = \[15,18] -> no overlap
  * merged = \[\[1,6], \[8,10], \[15,18]]

```java
class Solution {
    public int[][] merge(int[][] intervals) {
        
        if (intervals.length < 2) {
            return intervals;
        }
        
        Arrays.sort(intervals, (a,b) -> Integer.compare(a[0],b[0]));
        LinkedList<int[]> merged = new LinkedList();
        merged.add(intervals[0]);
        for(int i = 1; i < intervals.length; i++) {
            if (merged.getLast()[1] < intervals[i][0]) {
                merged.add(intervals[i]);
            } else {
                merged.getLast()[1] = Math.max(merged.getLast()[1], intervals[i][1]);
            } 
        }
        
        return merged.toArray(new int[merged.size()][]);
        
    }
}
```

A faster meahtod

```java
class Solution {
    public int[][] merge(int[][] intervals) {
        if (intervals.length < 2) {
            return intervals;
        }
        
        Arrays.sort(intervals, (a,b) -> Integer.compare(a[0], b[0]));
        LinkedList<int[]> ans = new LinkedList();
        
        int start = 0;
        int end = 1;
        
        for (int[] interval : intervals) {
            if (ans.isEmpty() || ans.getLast()[end] < interval[start]) {
                ans.add(interval);
            } else {
                ans.getLast()[end] = Math.max(ans.getLast()[end], interval[end]);
            }
        }
        
        return ans.toArray(new int[ans.size()][]);
        
    }
}
```

