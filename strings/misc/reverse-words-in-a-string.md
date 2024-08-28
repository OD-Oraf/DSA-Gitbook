# Reverse Words in a String

```java
class Solution {
    public String reverseWords(String s) {
        String[] words = s.trim().split(" ");
        StringBuilder result = new StringBuilder();
        
        for (int i = words.length - 1; i >= 0; i--) {
            if (!words[i].isEmpty()) {//valid word
                result.append(words[i]).append(" ");
            }
        }
        
        return result.toString().trim();
        
    }
}
```
