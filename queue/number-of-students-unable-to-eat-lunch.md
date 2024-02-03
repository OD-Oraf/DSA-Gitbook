# Number of students unable to eat lunch

Link: [https://leetcode.com/problems/number-of-students-unable-to-eat-lunch/](https://leetcode.com/problems/number-of-students-unable-to-eat-lunch/)

```java
class Solution {
    public int countStudents(int[] students, int[] sandwiches) {
        //Availabe sandwiches need to match student preferences
        
        int[] studentPreference = new int[]{0,0};
        for (int i = 0; i < students.length; i++) {
            studentPreference[students[i]] += 1;//update array with count of total preference for each sandwich type
        }
        
        int k = 0;
        while (k < sandwiches.length) {
            if (studentPreference[sandwiches[k]] > 0) {//if the current sandwich is prefernecce of anyone in the queue
                studentPreference[sandwiches[k]] -= 1;// remove them from the queue
                
            } else {
                break;
            }
            
            k++;
        }
        
        return sandwiches.length - k;// number of unchosen sandwiches
        
    }
}
```
