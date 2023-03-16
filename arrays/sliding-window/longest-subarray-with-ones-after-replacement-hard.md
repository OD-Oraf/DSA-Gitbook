# Longest Subarray with Ones after Replacement (hard)

## Strategy

* Keep count for number of ones in array.
* Find amount of zeroes in array by difference in number of ones and length of window
  * Shorten window if we exceed k zeros

```java
class ReplacingOnes {
  public static int findLength(int[] arr, int k) {
    // TODO: Write your code here
    int left = 0;
    int maxLength = 0;
    int onesCount = 0;

    for (int i = 0; i < arr.length; i++) {
      if (arr[i] == 1) {
        onesCount++;
      }
      int windowLength = i - left + 1;
      if (windowLength - onesCount > k) {
        if (arr[left] == 1) {
          onesCount--;
        }
        left++;
      }

      maxLength = Math.max(maxLength, i - left + 1);
    }

    return maxLength;
  }
}

```
