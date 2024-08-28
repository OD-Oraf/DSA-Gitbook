# Longest Consecutive Sequence



## Strategy - Use Hashset and visualize numbers on number line

* If you view all the numbers on a number line, you will see that the beginning of a sequence has no left boundary(no number to the left)
* The length of a sequence are the following consecutive number that are in the array converted to a set

### Time/Space

* Time
  * O(n)
* Space&#x20;
  * O(n) -> Extra space used in the Hashset conversion of the array

```java
class Solution {
    public int longestConsecutive(int[] nums) {
        if (nums.length == 0) {
            return 0;
        }
        
        HashSet<Integer> set = new HashSet();
        for (int num : nums) {
            set.add(num);
        }
        
        int maxLen = 1;// global max
        
        for (int num : nums) {
            if (!set.contains(num - 1)) {
                int currLen = 1;
                while (set.contains(num + 1)) {
                    num++;
                    currLen++;
                }
                maxLen = Math.max(maxLen, currLen);
            }
        }
        
        return maxLen;
        
    }
}

// More efficeint

class Solution {
    public int longestConsecutive(int[] nums) {
        if (nums.length < 2) {
            return nums.length;
        }
        
        int maxLen = 0;
        
        HashSet<Integer> set = new HashSet();
        for (int num : nums) {
            set.add(num);
        }
        
        for (int i = 0; i < nums.length; i++) {
            int currLen = 1;//nums[i] counts as 1
            //check left
            int num = nums[i];
            while (set.contains(--num)) {
                currLen++;
                set.remove(num);
            }
            
            //check right
            num = nums[i];
            while (set.contains(++num)) {
                currLen++;
                set.remove(num);
            }
            
            maxLen = Math.max(maxLen, currLen);
        }
        
        return maxLen;
        
    }
}
```
