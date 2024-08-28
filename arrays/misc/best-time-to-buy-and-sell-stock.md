# Best time to buy and sell stock

## Question Link

[https://leetcode.com/problems/best-time-to-buy-and-sell-stock/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)

#### Important Java feature (not necessary but useful)

`Integer.MAX_VALUE`

## Strategy - One Pass&#x20;

* 2 Main points
  * At each step check the current profit against the max profit
  * Also check the current minimum against the global min
* Keep track of&#x20;
  * maxProfit
  * globalMin

### Time COmplexity -&#x20;

* TIme
  * O(n)
  * One pass so we operate on n elements
* Space
  * O(1)&#x20;
  * No additional space used

```java
class Solution {
    public int maxProfit(int[] prices) {
        int globalMin = prices[0];
        int maxProfit = 0;
        
        for (int i = 1; i < prices.length; i++) {
            if (prices[i] < globalMin) {
                globalMin = prices[i];
                // System.out.println(prices[i]);
                continue;
            }
            
            maxProfit = Math.max(maxProfit, prices[i] - globalMin);
            // System.out.println(prices[i] - globalMin);
            
        }
        
        return maxProfit;
    }
}
```

## Strategy - Kadanes Algorithms

* The goal is to turn the problem into "max subarray"
* This is done by converting the array of prices into a **difference between prices** array&#x20;
  * Each index in prices\[i] - prices\[i - 1]
* Example
  * Prices = (1,7,4,11)&#x20;
  * differences of prices = (0, 6, -3, 7)

```java
  public int maxProfit(int[] prices) {
        int currMax = 0, maxSoFar = 0;
        for(int i = 1; i < prices.length; i++) {
            currMax = Math.max(0, currMax += prices[i] - prices[i-1]);
            maxSoFar = Math.max(currMax, maxSoFar);
        }
        return maxSoFar;
    }
```

## Strategy - Brute Force

### Time complexity -

* Time&#x20;
  * O(n^2) -> loop runs n(n-1)/2 times
* Space
  * O(1)&#x20;
  * Only two variables used

```java
public class Solution {
    public int maxProfit(int prices[]) {
        int maxprofit = 0;
        for (int i = 0; i < prices.length - 1; i++) {
            for (int j = i + 1; j < prices.length; j++) {
                int profit = prices[j] - prices[i];
                if (profit > maxprofit)
                    maxprofit = profit;
            }
        }
        return maxprofit;
    }
}
```
