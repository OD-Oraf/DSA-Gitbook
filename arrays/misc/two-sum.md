# Two Sum

## Question Link

[https://leetcode.com/problems/two-sum/](https://leetcode.com/problems/two-sum/)

#### Important Java features

```
map.containsKey()
map.put()
return new int[]{}
```

## Strategy (2 pass Hashmap)

* Parse array and push to hashmap
* Parse array again and see if complement exists in array
  * Make sure if complement exists, it doesn't refer to the original number. Ex don't want same number doubled to equal target



```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        // Store numbers in hashmap 
        // FOr each number calulate the complement and check the map
        // If matching make sure it isnt the same index so we cant use
        // same number twice
        
        // Populate Map 
        HashMap<Integer, Integer> map = new HashMap();
        for (int i = 0; i < nums.length; i++) {
            map.put(nums[i], i);
        }
        
        for (int i = 0; i < nums.length; i++) {
            int complement = target - nums[i];
            
            if (map.containsKey(complement) && map.get(complement) != i) {
                return new int[] {i, map.get(complement)};
            }
        }
        
        return new int[] {};
        
    }
}

```

### Time/Space Complexity

Time: O(n) - Traverse list of n elements twice. Hashmap lookup time is O(1)

Space: O(n) - Space depends on number of elements stored in hash table which at worst case is n&#x20;

## Strategy (1 pass Hashmap)

* We actually don't need to store all the numbers in the hashmap before we check for complements
* While inserting elements into the map we can check if the current indexes complement is existing.&#x20;
* How do we avoid duplication?
  * We will always check the complement against the map. If we get a match, the same index cant be used because it would have come from a previous iteration when pushed to the map
  * EX

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        // One pass hashtable
        HashMap<Integer, Integer> map = new HashMap(); // <Number, Index>
        
        for (int i = 0; i < nums.length; i++) {
            int complement = target - nums[i];
            if (map.containsKey(complement)) {
                return new int[] {map.get(complement), i};
            }
            
            map.put(nums[i], i);
        }
        
        return new int[] {-1, -1};
    }
}

/* [2,7,11,15]
target = 9
0 : complement - 7, map{2:0}
1 : complement - 2, 


EX.
[2,3,3,15]
target = 6

Math at i = 2 because complement, 3, is already therre
At i = 1, complement is not existing in the map 
*/
```
