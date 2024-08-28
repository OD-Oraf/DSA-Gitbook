# Can Place Flowers



```java
class Solution {
    public boolean canPlaceFlowers(int[] flowerbed, int n) {
        // No flowers in adjacent plots
        // Return true if n new flowers can be planted
        // Eveerytime we find a valid plot -> set 1 and decrease n 
            // At end return if n == 0 
        
        if (n == 0) {
            return true;
        }
        int size = flowerbed.length;
                                                            
        for (int i = 0; i < flowerbed.length; i++) {
            if (
                flowerbed[i] == 0 && 
                (i == size - 1 || flowerbed[i + 1] == 0) && // edge case geginnig s 
                (i == 0 || flowerbed[i - 1] == 0)
            ) {
                flowerbed[i] = 1;
                n--;
                if (n == 0) {
                    return true;
                }
            }
        }
        
        return false;
        
    }
}
```
