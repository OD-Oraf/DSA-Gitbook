# Bag Of Tokens

## Strategy - Sort and use two pointer to go trough tokens

**What patterns do we notice in how the tokens are played to maximize the score in the above examples?**

* The lowest power tokens are played face-up to increase the score.
* The highest power tokens are played face-down to increase power.

**We can develop a strategy based on these observations:**

* When you have enough power to play face-up, maximize the score by playing the lowest power tokens face-up. This way you are increasing the score without losing a significant amount of power.
* When you do not have enough power to play face-up, maximize power by playing the highest power tokens face-down. This way you trade a relatively small amount of score for a relatively large amount of power.
* We should play the lowest tokens face-up until we do not have enough power, then play token(s) face-down until we can play face-up again.
* We continue while we can either play a token face-up or face-down.

```java
class Solution {
    public int bagOfTokensScore(int[] tokens, int power) {
        /*
        Sort tokens from low to high and use
        Use low token to add to score for min cost for score(could be waseted on power)
        Use high token to add to power for min cost to power(would be wasted for score but would cost too much, better to use for iuncreasing power)
    
        */
        
        int low = 0;
        int high = tokens.length - 1;
        int score = 0;
        
        Arrays.sort(tokens);
        
        while(low <= high) {
            if (power >= tokens[low]) {// Use low tokens to add to score
                score += 1;
                power -= tokens[low];
                low++;
            } else if (low < high && score > 0) {
                score -= 1;
                power += tokens[high];
                high--;
            } else {
                return score;
            }
        }
        
        return score;
        
    }
}
```
