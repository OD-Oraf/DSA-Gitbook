# Contains Duplicate

## Strategy - Sort Array

* Sort array and check but very slow
* Can also use hash map to check for duplicates

### Time Complexity

* Time - O(nlog(n))
  * Time required to sort entire array
* Space O(1)
  * Depends on sorting array but costs O(1) if heapsort is used

```java
class Solution {
    public boolean containsDuplicate(int[] nums) {
        if (nums.length == 1) {
            return false;
        }
        
        Arrays.sort(nums);
        
        for (int i = 0; i < nums.length - 1; i++) {
            if (nums[i] == nums [i + 1]) {
                return true;
            }
        }
        
        return false;
        
    }
}
```

## Strategy - (HashSet)

* Use hashset to keep track of unique numbers
* If number is already existing in set then we know the duplicate exists

### Time Complexity

* Time - O(n)
* Space - O(n) Space used by a hash set is linear with number of elements

```java
class Solution {
    public boolean containsDuplicate(int[] nums) {
        
        Set<Integer> set = new HashSet();
        
        for (int num : nums) {
            if (set.contains(num)) {
                return true;
            } 
            set.add(num);
        }
        
        return false;
        
    }
}
```

## Strategy - Naive Approach

* Use nested for loop to compare all possible combinations



### Time Complexity

* Time
  * O(n^2)
* Space&#x20;
  * O(1)

```java
class Solution {
    public boolean containsDuplicate(int[] nums) {
        
        HashSet<Integer> set = new HashSet<>();
        
        for (int num : nums) {
            if (!set.contains(num)) {
                set.add(num);
            } else {
                return true;
            }
        }
        
        return false;
        
    }
}
```
