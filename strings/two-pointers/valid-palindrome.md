# Valid Palindrome

## Strategy

* Use two pointer strategy
* Remember to&#x20;
  * Lowercase characters
  * Ignore elements that aren't a letter



### Important

* Check variable names, left/right VS p1/p2 VS start/end

```java
Character.toLowerCase()
Characer.isLetterOrDigit()
```



<pre class="language-java"><code class="lang-java"><strong>// Cleaner Solution, Faster
</strong><strong>class Solution {
</strong>    public boolean isPalindrome(String s) {
        if (s.isEmpty()) {
        	return true;
        }
        int left = 0;
        int right = s.length() - 1;
        while(left &#x3C;= right) {
        	char charLeft = s.charAt(left);
        	char charRight = s.charAt(right);
        	if (!Character.isLetterOrDigit(charLeft)) {
        		left++;
        	} else if(!Character.isLetterOrDigit(charRight)) {
        		right--;
        	} else {
        		if (Character.toLowerCase(charLeft ) != Character.toLowerCase(charRight)) {
        			return false;
        		}
        		left++;
        		right--;
        	}
        }
        return true;
    }
}
</code></pre>

<pre class="language-java"><code class="lang-java">// Same thing but uses continue instead of if/else
<strong>class Solution {
</strong>    public boolean isPalindrome(String s) {
        // Use two pointers at start and end of word
        
        // EIther empty or one character
        if (s.length() &#x3C;= 1) {
            return true;
        }
        
        s.toLowerCase();
        
        int p1 = 0;
        int p2 = s.length() - 1;
        // make lowercase
        
        while (p1 &#x3C; p2) {
            char start = Character.toLowerCase(s.charAt(p1));
            char end = Character.toLowerCase(s.charAt(p2));
             
            //skip invalid chracers from left
            if (!Character.isLetterOrDigit(start)) {
                p1++;
                continue;
            }
            //skip invalid characters from right
            if (!Character.isLetterOrDigit(end)) {
                p2--;
                continue;
            }
            
            if (start != end) {
                return false;
            }
            p1++;
            p2--;
        }
        
        return true;
        
    }
}
</code></pre>
