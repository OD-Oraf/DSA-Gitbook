# Longest Palindrome

[https://leetcode.com/problems/longest-palindrome/submissions/](https://leetcode.com/problems/longest-palindrome/submissions/)

## Strategy - Char frequency array

* Create a char frequency array to keep count of each character
* result += (charCount/2) + 2 rounds down to the even number for palindrome
* If result is even and a charCount is odd then we can add one character for the middle of the palindrome
  * This can only be done once

```java
class Solution {
    public int longestPalindrome(String s) {
        // Use hashmap 
        int[] charCounts = new int[128];
        int result = 0;
        for (char c: s.toCharArray()) { // populate charCount
            charCounts[c]++; // Count letters by converting to ascii and updating that index
        }
        
        for (Integer charCount : charCounts) {
            result += (charCount/2) * 2; // only take even cunt from each charCount
            if (result % 2 == 0 && charCount % 2 == 1) {// only runs once
                result += 1;
            }
        }
        
        return result;
        
    }
}
```

## Strategy - HashSet(Not as efficient)&#x20;

* If current element is already existing in hashset, remove it and update the count since removal implies a pair
  * Otherwise add that element to the hashset
* At the end if the hashset still isn't empty, one of the elements can be used as the middle of the palindrome so add 1 to the count\*2
  * &#x20;Otherwise just return count\*2

```java
class Solution {
    public int longestPalindrome(String s) {
        if (s.length() == 0 || s == null) {
            return 0;
        }
        
        HashSet<Character> set = new HashSet<>();
        int count = 0;
        for (char c : s.toCharArray()) {
            if (set.contains(c)) {
                set.remove(c);
                count++;
            } else {
                set.add(c);
            }
        }
        
        if (!set.isEmpty()) {
            return (count * 2) + 1;
        } 
        return count * 2;
        
    }
}
```
