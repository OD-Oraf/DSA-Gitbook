# Longest Substring with Same Letters after Replacement(Sliding Window)

This problem follows the **Sliding Window** pattern, and we can use a similar dynamic sliding window strategy as discussed in [Longest Substring with Distinct Characters](https://www.educative.io/courses/grokking-the-coding-interview/YMzBx1gE5EO). We can use a HashMap to count the frequency of each letter.

* We will iterate through the string to add one letter at a time in the window.
* We will also keep track of the count of the maximum repeating letter in **any** window (let’s call it `maxRepeatLetterCount`).
* So, at any time, we know that we do have a window with one letter repeating `maxRepeatLetterCount` times; this means we should try to replace the remaining letters.
  * If the remaining letters are less than or equal to `k`, we can replace them all.
  * If we have more than `k` remaining letters, we should shrink the window as we cannot replace more than `k` letters.

While shrinking the window, we don’t need to update `maxRepeatLetterCount` (hence, it represents the maximum repeating count of ANY letter for ANY window). Why don’t we need to update this count when we shrink the window? Since we have to replace all the remaining letters to get the longest substring having the same letter in any window, we can’t get a better answer from any other window even though all occurrences of the letter with frequency `maxRepeatLetterCount` is not in the current window.

```java
class CharacterReplacement {
  public static int findLength(String str, int k) {

    HashMap<Character, Integer> map = new HashMap<>(); 
    int maxLen = 0;
    int left = 0;
    int maxRepeatLetterCount = 0;

    for (int i = 0; i < str.length(); i++) {
      char c = str.charAt(i);
      map.put(c, map.getOrDefault(c, 0) + 1);
      maxRepeatLetterCount = Math.max(maxRepeatLetterCount, map.get(c));
      
      if (i - left + 1 - maxRepeatLetterCount > k) {
        char leftChar = str.charAt(left);
        map.put(leftChar, map.get(leftChar) - 1);
        left++;
      }

      maxLen = Math.max(maxLen, i - left + 1);
    }

    return maxLen;

  }
}

```

