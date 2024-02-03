# Subsets

Link: [https://leetcode.com/problems/subsets/](https://leetcode.com/problems/subsets/)

## Strategy Backtracking

* Time Complexity
  * O(n\*2^n)
  * 2^n # of subsets
  * at most n numbers in a set

```java
// Solution 1
class Solution {
    public List<List<Integer>> subsets(int[] nums) {
        List<List<Integer>> ans = new ArrayList<>();
        // List<Integer> curr = new ArrayList<>();
        backtrack(new ArrayList(), ans, nums, 0);
        return ans;
        
    }
    
    public void backtrack(List<Integer> curr, List<List<Integer>> ans, int[] nums, int start) {
        
        ans.add(new ArrayList<>(curr));
        
        for (int i = start; i < nums.length; i++){
            curr.add(nums[i]);
            backtrack(curr, ans, nums, i + 1);
            curr.remove(curr.size() - 1);
        }
    }
}





//Solution 2
class Solution {
    List<List<Integer>> ans = new ArrayList<>();
    int n;
    int setSize;
    
    public List<List<Integer>> subsets(int[] nums) {
        n = nums.length;
        for (setSize = 0; setSize < n + 1; ++setSize) {
            backtrack(0, new ArrayList<Integer>(), nums);
        }
        return ans;
    }
    
    public void backtrack(int first, ArrayList<Integer> curr, int[] nums) {
        if (curr.size() == setSize) {
            ans.add(new ArrayList(curr));
            return;
        }
        for (int i = first; i < n; ++i) {
            curr.add(nums[i]);
            backtrack(i + 1, curr, nums);
            curr.remove(curr.size() - 1);
        }
    }
}
```
