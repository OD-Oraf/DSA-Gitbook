# Product of Array Except Self

## Strategy - Brute Force

* The idea here is that for each index of "i" multiply to get the total product
  * Skip self by continuing on i == j&#x20;
* Time Complexity -> O(n^2)
* Space -> O(1)

```java
class Solution {
    public int[] productExceptSelf(int[] nums) {
        int n = nums.length;
        int ans[] = new int[n];
        
        for(int i = 0; i < n; i++) {
            int product = 1;
            for(int j = 0; j < n; j++) {
                if(i == j) continue;
                product *= nums[j];
            }
            ans[i] = product;
        }
        
        return ans;
    }
}
```

## Strategy - Divide the total product by each number

* Get total product of array and divide for num in each index
* IMPORTANT -> Does not work if array contains 0

```java
class Solution {
    public int[] productExceptSelf(int[] nums) {
        int n = nums.length;
        int ans[] = new int[n];
        int pro = 1;
        for(int i : nums) {
            pro *= i;
        }
        
        for(int i = 0; i < n; i++) {
            ans[i] = pro / nums[i];
        }
        return ans;
    }
}
```

## Strategy - prefix and postfix arrays

* Traverse the array twice, forwards and backwards
* Create prefix product array by multiplying the last index of nums  by the previous prefix product
* Create suffix product array by doing the same in reverse at the end of the nums array
* Prefix contains product of each number before i and post fix contains product of each number after i

### Time complexity -&#x20;

* Time - O(n)
  * Traversing array twice so more like O(2n)
* Space - O(n)&#x20;
  * Using extra space for prefix and postfix arrays

```java
class Solution {
    public int[] productExceptSelf(int[] nums) {
        
        
        int[] leftPrefix = new int[nums.length];
        int[] rightPostfix = new int[nums.length];
        int[] ans = new int[nums.length];
        
        //construct left prefix array
        leftPrefix[0] = 1;
        for (int i = 1; i < nums.length; i++) {
            leftPrefix[i] = leftPrefix[i - 1] * nums[i - 1];
        }
        
        //construct right postfix array
        rightPostfix[nums.length - 1] = 1;
        for (int i = nums.length - 2; i >= 0; i--){
            rightPostfix[i] = rightPostfix[i + 1] * nums[i + 1];
        }
        
        //ans array
        for (int i = 0; i < nums.length; i++) {
            ans[i] = leftPrefix[i] * rightPostfix[i];
        }
        
        return ans;
    }
}
```

## Strategy - Directly store product of prefix and suffix in ans

```java
class Solution {
    public int[] productExceptSelf(int[] nums) {
        //At each i going forwards, store prouct of all nums before i in i
        // At each i going backwards, store product of all nums after i in i

        int n = nums.length;
        int[] ans = new int[n];
        Arrays.fill(ans, 1);
        
        int prefix = 1;
        for(int i = 0; i < n; i++) {
            ans[i] *= prefix;// store cumulative prefix at i
            prefix *= nums[i]; // multiply prefix by ans[i] for i + 1
        }
        
        int postfix = 1;
        for(int j = n - 1; j >= 0; j--) {
            ans[j] *= postfix; // update cumulative prefix by cumulative postfix
            postfix *= nums[j]; // multiply post fix by ans[j] for j - 1
        }
        
        return ans;
        
    }
}
```
