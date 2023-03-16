# Two Sum

## Question Link

[https://leetcode.com/problems/two-sum/](https://leetcode.com/problems/two-sum/)

#### Important Java features

```
map.containsKey()
map.put()
return new int[]{}
```

## Strategy&#x20;

* Parse array and push to hashmap
* Parse array again and see if complement exists in array
  * Make sure if complement exists, it doesnt refer to the original number. Ex dont want same number doubled to equal target
*
* Keep track of&#x20;
  * maxProfit
  * globalMax
  * globalMin

The main idea of this problem is that you want to iterate through the list finding the smallest value and then finding the greatest value following that smallest value.&#x20;

Keep track of the smallest value in the array to find the global minimum. Initialize the global  minimum  as the maximum value for and integer and decrease with each iteration.



```java
package com.company.arrays;

public class BestTimeToBuyAndSellStock {
    private static int maxProfit(int[] prices){
        int maxProfit = 0;
        int globalMax = 0;
        int globalMin = Integer.MAX_VALUE;

        for (int i = 0; i < prices.length; i++) {
            if (prices[i] > globalMax) {
                globalMax = prices[i];
            }
            if (prices[i] < globalMin) {
                globalMin = prices[i];
                globalMax = prices[i];
            }
            maxProfit = Math.max(maxProfit, globalMax - globalMin);
        }
        return maxProfit;
    }
    public static void main(String[] args){

        int[] prices = {7,1,5,3,6,4};
        System.out.println(maxProfit(prices));

    }
}
```

