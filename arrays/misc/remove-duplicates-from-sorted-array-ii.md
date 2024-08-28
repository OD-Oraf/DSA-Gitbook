# Remove Duplicates from Sorted Array II

```javascript
// Some code
```

## Strategy - Remove duplicates by overwriting and shortening array

```java
class Solution {
    public int removeDuplicates(int[] nums) {
        // init counter index array
        int count = 1; 
        int i = 1;// start loop from second element
        int length = nums.length;
        while (i < length) {
            if (nums[i] == nums[i - 1]) {
                count++;
                if (count > 2) {
                removeElement(nums, i);
                i--;// adjust array to new length
                length--;
                } 
            } else {
                count = 1;
            }
                i++; //dont forget to index with while loop
            }
        return length;   
    }
    
    public int[] removeElement(int[] nums, int index) {
        //overwrite element by shifting one position to the right
        for (int i = index + 1; i < nums.length; i++) {
            nums[i - 1] = nums[i];
        }
        return nums;
    }
}
```

## Strategy - Keep track of last valid index

```java
class Solution {
    public int removeDuplicates(int[] nums) {
        if (nums.length == 2) {
            return nums.length;//allows duplicate value
        }   
        int curr = 2;
        int lastValidIndex = 1;
        
        while (curr < nums.length) {
            if (nums[curr] == nums[lastValidIndex] && nums[curr] == nums[lastValidIndex - 1]) { // if curr is equal to the previous 2 values > skip the duplicate
                curr++; // skip current value
            } else {
                // update value after lastValidIndex
                lastValidIndex++;
                nums[lastValidIndex] = nums[curr];
                curr++;
            }
                
        }
        
        return lastValidIndex + 1;
    }
}
```

## Strategy - Generic Solution for duplicates\\

```java
class Solution {
    public int removeDuplicates(int[] nums) {
    		//define at most k times of duplicate numbers
    		final int k = 2;

    		//check if it is an empty array
    		if(nums.length == 0) return 0;

    		//0ne plus ending index of array w/o duplicates -> simmular to swap point while i finds next valid
    		int m = 1;

    		// count the time of duplicate numbers occurence
    		int count = 1;

    		for(int i = 1; i < nums.length; i++) {
    			if(nums[i] == nums[i - 1]) {
    				if(count < k) {
    					nums[m++] = nums[i];
    				}
    				count++;
    			} else {
    				count = 1;
    				nums[m++] = nums[i];
    			}
    		}
    		return m;
    	}
}
```
