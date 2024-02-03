# Capacity To Ship Packages Within D Days

[https://leetcode.com/problems/capacity-to-ship-packages-within-d-days/](https://leetcode.com/problems/capacity-to-ship-packages-within-d-days/)

## Strategy - Binary Search

* We use a binary search approach to find the least weight capacity that allows all the packages to be shipped within the given days ammount
* Binary search values range from min(largest weight) to max(sum of all weights)
  * Min values allow at least 1 package per day
  * Max value allows all packages to be sent in one daynary Tree&#x20;

```java
class Solution {
    
    Boolean validCapacity(int[] weights, int c, int shipsAvailable) {
        int shipsNeeded = 1;
        int currentLoad = 0;
        for (int weight : weights) {
            currentLoad += weight;
            if (currentLoad > c) {//if exceeding current capacity
                shipsNeeded++;
                currentLoad = weight;
            }
        }
        return shipsNeeded <= shipsAvailable;
    }
    public int shipWithinDays(int[] weights, int days) {
        /*
        Think about min and max capacities
        min will be the max weight and max is the sum of weigths
        */
        
        int minCapacity = weights[0];
        int maxCapacity = 0;
        for (int weight : weights) {
            minCapacity = Math.max(minCapacity, weight);
            maxCapacity += weight;
        }
        
        int left = minCapacity;
        int right = maxCapacity;
        
        while (left < right) {
            int mid = (left + right) / 2;
            if (validCapacity(weights, mid, days)) {
                right = mid;
            } else {
                left = mid + 1;
            }
        }
        
        return left;
        
    }
}
```
