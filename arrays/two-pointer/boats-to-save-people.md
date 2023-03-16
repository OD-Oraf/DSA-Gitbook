# Boats to Save people

```java
class Solution {
    public int numRescueBoats(int[] people, int limit) {
        
        Arrays.sort(people);
        
        int heavyIndx = people.length - 1;
        int lightIndx = 0;
        int minBoats = 0;
        
        while (lightIndx <= heavyIndx) {
            if (people[heavyIndx] + people[lightIndx] <= limit) {
                heavyIndx--;
                lightIndx++;
                minBoats++;
            } else {
                heavyIndx--;
                minBoats++;
            }
        }
        
        return minBoats;
        
    }
}
```
