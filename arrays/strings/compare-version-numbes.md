# Compare Version Numbes



## Strategy - Separate Versions into String\[] and compare

```java
class Solution {
    public int compareVersion(String version1, String version2) {
        //separate each version into sections and compare each
        
        String[] v1Section = version1.split("\\.");//spit version into sections
        String[] v2Section = version2.split("\\.");
        
        int v1Len = v1Section.length;//Lengt of section
        int v2Len = v2Section.length;
        int p1 = 0;//get pointers to check valid indicies
        int p2 = 0;
        
        while (p1 < v1Len || p2 < v2Len) { // continue length of longest number
            int v1 = p1 < v1Len ? Integer.parseInt(v1Section[p1]) : 0;// if index is still valid number then set v1 to that number other wise set to 0 for comparison
            int v2 = p2 < v2Len ? Integer.parseInt(v2Section[p2]) : 0;
            
            if (v1 != v2) { // if not equal, return number based on comparison
                return v1 < v2 ? -1 : 1;
            }
            
            if (p1 < v1Len) p1++; //increment if p1 hasnt reached end
            if (p2 < v2Len) p2++;
        }
        
        return 0;
        
    }
}
```
