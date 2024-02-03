# Majority Element

### Strategy (Sorting)

* With the sorting strategy, since the majority element is at least n/2 that means it takes up the majority of the sorted arrays. Whether it starts at the beginning or finishes at the end, the midpoint will always return the majority element

```java
class Solution {
    public int majorityElement(int[] nums) {
        Arrays.sort(nums);
        
        return nums[nums.length / 2];
        
    }
}
```

## Strategy - HashMap(Record number frequency)

* Create a hashmap and record the frequency of each number.&#x20;
* Iterate though the keyset and update the majority element accordingly
* Remember to set majority to first number and3

```java
class Solution {
    public int majorityElement(int[] nums) {
        
        if (nums.length < 2) {
            return nums[0];
        }
        
        HashMap<Integer, Integer> map = new HashMap();
        for (int num : nums) {
            map.put(num, map.getOrDefault(num, 0) + 1);
        }
        
        int majority = nums[0];
        for (int key : map.keySet()) {
            if (map.get(key) > map.get(majority)) {
                majority = key;
            }
        }
        
        return majority;
        
    }
}
```

### Strategy - Boyer-Moore majority vote algorithm

* Conditions to be aware of
  * If current number is different from the previous decrease count
  * If count hits 0 update candidate to current element and set count to 1

```java
class Solution {
    public int majorityElement(int[] nums) {
        // Boyer-Moore Majority Vote algorithm
        
        // current cadiddate for majority elm
        
        if (nums.length < 2) {
            return nums[0];
        }
        int candidate = nums[0]; 
        int count = 1;
        
        for (int i = 1; i < nums.length; i++) {
            if (nums[i] != candidate) {
                count--;
            }
            if (count == 0) {
                candidate = nums[i];
            }
            
            if (nums[i] == candidate) {
                count++;
            }   
        }
        return candidate;
    }
}
```
