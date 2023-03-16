# Triplet Sum to Zero

## Strategy

* X + Y + Z = 0 -becomes&#x20;
* Y + Z == -X
* Find pair matching negative complement

### Time Complexity

Sorting the array will take O(N \* logN)O(N∗logN). The `searchPair()` function will take O(N)O(N). As we are calling `searchPair()` for every number in the input array, this means that overall `searchTriplets()` will take O(N \* logN + N^2)O(N∗logN+N2), which is asymptotically equivalent to O(N^2)O(N2).

### Space Complexity

Ignoring the space required for the output array, the space complexity of the above algorithm will be O(N) O(N) which is required for sorting.

### Inefficient solution

```java
import java.util.*;

class TripletSumToZero {

  public static List<List<Integer>> searchTriplets(int[] arr) {
    List<List<Integer>> triplets = new ArrayList<>();
    Arrays.sort(arr);
    // sort array 
    // for each complement binary search for pair

    if (arr.length == 0) {
      return triplets;
    }
    
    
    for (int i = 0; i < arr.length - 2; i++) {
      int complement = -arr[i];
      while (i > 0 && arr[i] == arr[i - 1]) {
        continue;
      }
      findPair(complement, i + 1, arr, triplets);
    }
    return triplets;
  }

  public static void findPair(int complement, int left, int[] arr, List<List<Integer>> triplets) {
    int right = arr.length - 1;

    while (left < right) {
      int leftVal = arr[left];
      int rightVal = arr[right];
      int currSum = leftVal + rightVal;

      if (currSum == complement) {
        triplets.add(Arrays.asList(-complement, leftVal, rightVal));
        left++;
        right--;
        while (left < right && arr[left] == arr[left - 1]) {
          left++; // skip duplicates on left
        }
        while (left < right && arr[right] == arr[right + 1]) {
          right--; // skip duplicates on right
        }
      } else if (currSum > complement) {
        right--;
      } else {
        left++; 
      }
    }

  }
}
```
