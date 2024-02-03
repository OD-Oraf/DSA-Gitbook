# Group Anagrams

### Strategy - Group by sorted strings

* Create arraylist for result and hashmap to contains mappings for sorted anagrams
* Use sorted anagram as a key and add all that math the pattern for that key
* Important methods

### Important methods

```java
// 2D HashMap
List<List<String>> res = new ArrayList();

// Map of String to arraylist
Map<String, List<String>> map = new HashMap();

// Convert String character array
char[] sArray = s.toCharArray();

// Cast character array to string
String sorted = new String(sArray);

// Put all values from map into arraylsit
res.addAll(map.values());
```

### Code Solution

<pre class="language-java"><code class="lang-java"><strong>class Solution {
</strong>    public List&#x3C;List&#x3C;String>> groupAnagrams(String[] strs) {
        List&#x3C;List&#x3C;String>> res = new ArrayList&#x3C;>();
        Map&#x3C;String, List&#x3C;String>> map = new HashMap();
        for (String s : strs) {
            char[] sArray = s.toCharArray();
            Arrays.sort(sArray);
            String sorted = new String(sArray);
            if (!map.containsKey(sorted)) {
                map.put(sorted, new ArrayList());
            }
            
            map.get(sorted).add(s);
        }
        res.addAll(map.values());
        return res;
    }
}
</code></pre>

## Time/Space Complexity

Time: O(NKlogK) -> N is length of strs and k is maximum length of a string in strs

* Outer loop(going through strings in strs) has complexity O(N) while sorting each string is O(K log K) time

Space: O(NK) total information stored in ans



## Strategy - Create mapping based on letter count(Inefficient)

```java
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        //Create key based on characer counts
        
        // List<List<String>> map = new ArrayList();
        HashMap<String,List<String>> map = new HashMap<>(); 
        
        //reuse this same array for each word
        int[] charCount = new int[26];
        for (String s : strs) {
            //set up keys with character counts
            Arrays.fill(charCount, 0);
            for (char c : s.toCharArray()) {
                charCount[c - 'a']++;//increment value based on index which represents ezch character a:0 z:25
            }
            
            StringBuilder sb = new StringBuilder("");//create mapping of charCount
            for (int i = 0; i < 26; i++) {
                sb.append(charCount[i]);
                sb.append('#');
            }
            String stringKey = sb.toString();
            
            if (!map.containsKey(stringKey)) {
                map.put(stringKey, new ArrayList());
            }
            map.get(stringKey).add(s);
        }
       return new ArrayList(map.values());
        
        
    }
}
```
