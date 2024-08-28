# Valid Word Square

## Strategy - Use StringBuilder

* The idea is to create a separate function in which we get the col word and compare with the row word
* Go through each word and get the index of the current row words index

```java
class Solution {
    public boolean validWordSquare(List<String> words) {
        // COmparre row word to column word
        
        for (int i = 0; i< words.size(); i++) {
            String rowWord = words.get(i);
            if (!rowWord.equals(getColWord(i, words))) {
                return false;
            }  
        }
        
        return true;
        
    }
    
    public String getColWord(int colIndex, List<String> words) {
        StringBuilder colWord = new StringBuilder();
        for (int i = 0; i < words.size(); i++) {
            String rowWord = words.get(i);
            
            if(colIndex < rowWord.length()) {
                colWord.append(rowWord.charAt(colIndex));
            }
        }
        
        return colWord.toString();
        
    }
}
```
