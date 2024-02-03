# Koko Eating Bananas

{% embed url="https://leetcode.com/problems/koko-eating-bananas/" %}

## Strategy - Brute Force

* n piles
* ith pile has piles\[i] bananas
  * if piles\[i] < k then she will stop which means that she can eat at most 1 pile per hour
* len(p) <= h otherwise she doesnt have enough tine to eat each pile
  * (Since her max speed is 1 pile per hour)
* Hours per pile = #bananas/speed rouded up

```java
class Solution {
    public int minEatingSpeed(int[] piles, int h) {
        // Start at an eating speed of 1.
        int speed = 1;

        while (true) {
            // hourSpent stands for the total hour Koko spends with 
            // the given eating speed.
            int hourSpent = 0;

            // Iterate over the piles and calculate hourSpent.
            // We increase the hourSpent by ceil(pile / speed)
            for (int pile : piles) {
                hourSpent += Math.ceil((double) pile / speed);
                if (hourSpent > h) {
                    break;
                }
            }

            // Check if Koko can finish all the piles within h hours,
            // If so, return speed. Otherwise, let speed increment by
            // 1 and repeat the previous iteration.
            if (hourSpent <= h) {
                return speed;
            } else {
                speed += 1;
            }            
        }
    }
}
```

## Strategy - Binary Search

* For the binary search solution the fastest k value is the max value in the entire array
  * This allows her to reach the speed of 1 pile per hour
* Do a binary search from 1 - max(piles)
* The idea is to search far a valid speed, but also minimum. The binary search searches for the first valid speed which should be the minimum

### Space /Time

* Time - O(n\*logm)
  * n -> length of piles
  * m -> max num of bananas in one pile
  * Inital search spacce if 1 to m. Takes logm comparisons to reduce seaarch space to 1

```java
// midpoint 
midpoint  = (left + right) / 2;
// rounding up
Math.ceil((double) pile / speed);
```

```java
class Solution {
    public int minEatingSpeed(int[] piles, int h) {
        // Start at an eating speed of 1.
        // Arrays.sort(piles);
        
        int left = 1, right = 1;
        for (int pile : piles) {
            right = Math.max(right, pile);
        }
        

        while (left < right) {
            // Get the middle index between left and right boundary indexes.
            // hourSpent stands for the total hour Koko spends.
            int speed = (left + right) / 2; 
            int hourSpent = 0;

            // Iterate over the piles and calculate hourSpent.
            // We increase the hourSpent by ceil(pile / speed)
            for (int pile : piles) {
                hourSpent += Math.ceil((double) pile / speed);
            }

            // Check if middle is a workable speed, and cut the search space by half.
            if (hourSpent <= h) {
                right = speed;
            } else {
                left = speed + 1;
            }            
        }
        
        return right; 
    }
}
```

## Strategy - More efficient Binary Search

Math.ceil((double) pile / speed) is inefficinet

Use (pile + speed - 1) / speed instead

```java
class Solution {
    public int minEatingSpeed(int[] piles, int h) {
        // Start at an eating speed of 1.
        // Arrays.sort(piles);
        
        int left = 1, right = 1;
        for (int pile : piles) {
            right = Math.max(right, pile);
        }
        

        while (left < right) {
            int speed = (left + right) / 2; 
            // hourSpent stands for the total hour Koko spends with 
            // the given eating speed.
            int hourSpent = 0;

            // Iterate over the piles and calculate hourSpent.
            // We increase the hourSpent by ceil(pile / speed)
            for (int pile : piles) {
                hourSpent += (pile + speed - 1) / speed;
            }

            // Check if Koko can finish all the piles within h hours,
            // If so, return speed. Otherwise, let speed increment by
            // 1 and repeat the previous iteration.
            if (hourSpent <= h) {
                right = speed;
            } else {
                left = speed + 1;
            }            
        }
        
        return right; 
    }
}
```
