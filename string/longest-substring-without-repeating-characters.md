# Longest Substring Without Repeating Characters

Given a string `s`, find the length of the **longest substring** without repeating characters.

\
In this question, the keyword is the longest substring instead of subset, so it is a continuous range in the string.

We use the sliding window to solve this question. the range of the index is \[i, j]. the length of the range is the answer.

TC: O(n + d) d is the alphabet

SC: O(d)

```java
public int lengthOfLongestSubstring(String s) {
    if (s == null || s.length() == 0) {
        return 0;
    }
    
    Set<Character> set = new HashSet();
    int fast = 0;
    int slow = 0;
    int res = 0;
    
    while (fast < s.length()) {
        if (set.add(s.charAt(fast))) {
            fast++;
            res = Max.math(res, fast - slow);
        } else {
            set.remove(s.charAt(slow));
            slow++;
        }
    }
    return res;
}
```
