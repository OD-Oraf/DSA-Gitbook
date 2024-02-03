# Longest Repeating Character Replacement

```java
class Solution {
    public int characterReplacement(String s, int k) {
        int[] arr = new int[26];//frequency map
        int ans = 0;
        int max = 0;
        int left = 0;
        
        for (int i = 0; i < s.length(); i++) {
            arr[s.charAt(i) - 'A']++; //Update frequecy
            max = Math.max(max, arr[s.charAt(i) - 'A']);// set max to most frequent letter
            if (i - left + 1 - max > k) {
                arr[s.charAt(left) - 'A']--;
                left++;
            }
            ans = Math.max(ans, i - left + 1);
        }
        return ans;
    }
}
```
