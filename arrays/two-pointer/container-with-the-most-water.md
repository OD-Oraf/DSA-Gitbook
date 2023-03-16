# Container with the most water

Use two pointer strategy

```java
class Solution {
    public int maxArea(int[] height) {
        // Use 2 pointers
        // Use min of both heights and calulate areas to find max
        
        
        
        int left = 0;
        int right = height.length - 1;
        int maxVol = 0;
        
        while (left < right) {
            int h = Math.min(height[left], height[right]);
            int l = right - left;
            maxVol = Math.max(maxVol, h * l);
            
            if (height[left] < height[right]) {
                left++;
            } else {
                right--;
            }
        }
        
        return maxVol; 
    }
}
```
