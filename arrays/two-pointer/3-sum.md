# 3 Sum

## Strategy

* Sort array and for each unique number do binary search to find triplet
* Remember to skip duplicates

```java
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        
        Arrays.sort(nums);
        List<List<Integer>> triplets = new ArrayList<>();
        
        for (int i = 0; i < nums.length - 2; i++) {
            int complement = -nums[i];
            if (i > 0 && nums[i] == nums[i - 1]) {
                continue;
            } 
            findPair(nums, complement, i + 1, triplets);
            
        }
        return triplets;  
    }
    
    public static void findPair(int[] nums,int complement, int left, List<List<Integer>> triplets) {
        
        int right = nums.length - 1;
        // Binary Search
        while (left < right) {
            if (nums[left] + nums[right] == complement) {
                triplets.add(Arrays.asList(-complement, nums[left], nums[right]));
                left++;
                right--;
                while (left < right && nums[left] == nums[left - 1]) {
                    left++;
                }
                while (left < right && nums[right] == nums[right + 1]) {
                    right--;
                }
            } else if (nums[left] + nums[right] > complement) {
                right--;
            } else {
                left++;   
            }
        }
        
    }
}
```

```java
class TripletSumToZero {

  public static List<List<Integer>> searchTriplets(int[] arr) {
    Arrays.sort(arr);
    List<List<Integer>> triplets = new ArrayList<>();
    for (int i = 0; i < arr.length - 2; i++) {
      // skip duplicate for unique
      int complement = -arr[i];
      if (i > 0 && arr[i] == arr[i - 1]) // skip same element to avoid duplicate triplets
        continue;
      searchPair(arr, complement, i + 1, triplets);
    }

    return triplets;
  }

  private static void searchPair(int[] arr, int complement, int left, List<List<Integer>> triplets) {
    int right = arr.length - 1;
    while (left < right) {
      int currentSum = arr[left] + arr[right];
      if (currentSum == complement) { // found the triplet
        triplets.add(Arrays.asList(-complement, arr[left], arr[right]));
        left++;
        right--;
        while (left < right && arr[left] == arr[left - 1])
          left++; // skip same element to avoid duplicate triplets
        while (left < right && arr[right] == arr[right + 1])
          right--; // skip same element to avoid duplicate triplets
      } else if (complement > currentSum)
        left++; // we need a pair with a bigger sum
      else
        right--; // we need a pair with a smaller sum
    }
  }

  public static void main(String[] args) {
    System.out.println(TripletSumToZero.searchTriplets(new int[] { -3, 0, 1, 2, -1, 1, -2 }));
    System.out.println(TripletSumToZero.searchTriplets(new int[] { -5, 2, -1, -2, 3 }));
  }
}
```
