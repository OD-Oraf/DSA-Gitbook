---
description: https://leetcode.com/problems/word-break/
---

# Word Break

```java
class Solution {
    public boolean wordBreak(String s, List<String> wordDict) {
        boolean[] dp = new boolean[s.length() + 1];
        dp[s.length()] = true;

        for(int i = s.length()-1; i >= 0; i--) {
            for(String w : wordDict){
                if((i + w.length()) <= s.length() && s.startsWith(w, i)){// make sure word length its and the work matches
                    dp[i] = dp[i + w.length()];// think of setting valid path to end
                }
                if(dp[i]) { // no need to check other words if we found a match
                    break;
                }
            }
        }
        return dp[0];
    }
}

```
