# Container with the most water

Use two pointer strategy

```java
class Solution {
    public int maxArea(int[] height) {
        // Find max area of water
        // H can only be at most the height of the shorter side
        
        int maxArea = 0;
        int left = 0;
        int right = height.length - 1;
    
        while (left < right) {
            int h = Math.min(height[left], height[right]);
            int w = right - left;
            int area = w * h;
            
            maxArea = Math.max(maxArea, area);
            
            if (height[left] <= height[right]) {
                left++;
            } else {
                right--;
            }
        }
        
        return maxArea;
        
    }
}
```
