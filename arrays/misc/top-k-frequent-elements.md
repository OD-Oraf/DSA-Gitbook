# Top K Frequent Elements

## Strategy - Get most frequent elements by bucket

Indices of the bucket(array) will represent the frequency counts of each number.

Helpful function

<pre class="language-java"><code class="lang-java"><strong>// Create ArrayList of integer arrays
</strong><strong>ArrayList&#x3C;Integer>[] buckets = new ArrayList[nums.length + 1];
</strong></code></pre>

### Time & Space

* Time O(n) -> List is iterated through multiple times&#x20;
* Space O(n)-> Extra space used for the HashMap as well as bucket array

```java
class Solution {
    public int[] topKFrequent(int[] nums, int k) {
        
        HashMap<Integer, Integer> freqMap = new HashMap<>();
        List<Integer>[] bucket = new List[nums.length + 1];// +1 is needed in case nums is size 1
        
        for (int num : nums) {
            freqMap.put(num, freqMap.getOrDefault(num, 0) + 1);//get frequency count for each number 
        }
        
        for (int key : freqMap.keySet()) {//Create array where idicies are freq and values are nums
            int freq = freqMap.get(key);//indicies of bucket represent frequencies
            if (bucket[freq] == null) {
                bucket[freq] = new ArrayList<>();
            }
            bucket[freq].add(key);
        }
        
        // Create res for output 
        int[] res = new int[k];
        int j = 0;  //used to update indicies in res array
        for (int i = nums.length; i >=0; i--) {// remember nums.length needed for last element
            if (bucket[i] == null) {
                continue;
            }
            for (int n : bucket[i]) {
                res[j++] = n;
                if (j == k) {
                    return res;
                }
            }
        }
        
        return res; 
    }
}

```
