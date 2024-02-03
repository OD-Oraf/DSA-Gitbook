# Kth Missing Positive Number

[https://leetcode.com/problems/kth-missing-positive-number/](https://leetcode.com/problems/kth-missing-positive-number/)

## Strategy - Brute force

* arr\[0] - 1 = number of positive integers before nums\[0]

```java
class Solution {
    public int findKthPositive(int[] arr, int k) {
        // keep track # of positive elements thorughout
        // arr[0] - 1 = # of positive elemetns before arr[0]
        // normally it would be arr[0] but were removing 0 from count
        
        if (k <= arr[0] - 1) {
            return k;
        }
        
        k -= arr[0] - 1;
        
        for (int i = 0; i < arr.length - 1; i++) {
            int missingNums = arr[i+1] - arr[i] - 1;//difference of 1 just means adjacent numbers but 0 nums between
            if (k <= missingNums) {
                return k + arr[i];//will never reach arr[i+1] because of transitive property
            }
            
            k -= missingNums;//update count k
        }
        
        return k + arr[arr.length - 1];//k + last elemet of array
        
    }
}
```
