# Permutations

Link: [https://leetcode.com/problems/permutations/](https://leetcode.com/problems/permutations/)

Note - Combinations vs permutations

* Combinations -> order does not matter
* Permutations -> order matters

## Strategy - Backtracking



### Time Complexity

Time: O(n\*n!)



```java
class Solution {
    public List<List<Integer>> permute(int[] nums) {
        List<List<Integer>> ans = new ArrayList<>();
        List<Integer> curr = new ArrayList<>();
        backtrack(curr, ans, nums);
        return ans;
        
    }
    
    public void backtrack(List<Integer> curr, List<List<Integer>> ans, int[] nums) {
        if (curr.size() == nums.length) {
            ans.add(new ArrayList<>(curr));
            return;
        }
        
        for (int num : nums) {
            if (!curr.contains(num)) {
                curr.add(num);
                backtrack(curr,ans, nums);
                curr.remove(curr.size() - 1);
            }
        }
    }
}
```
