# Boats to Save people

## Strategy - Two Pointer

* Its important to node that the largest weight will never exceed limit
* If we sort and use two pointers, we can use sum of smallest and largest and count boats that way

```java
class Solution {
    public int numRescueBoats(int[] people, int limit) {
        // two pointer going inwards
        Arrays.sort(people);
        
        int left = 0;
        int right = people.length - 1;
        int res = 0;
        
        while (left <= right) {
            
            if (people[right] + people[left] > limit) {// can only use right
                right--;
                res++;
            } else {
                right--;
                left++;
                res++;
            }
            
        }
        
        return res;
    }
}
```
