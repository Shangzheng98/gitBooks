# LeetCode-Longest Palindromic Substring

Given a string `s`, return _the longest palindromic substring_ in `s`.



For this question, we can check each element as the center from the center to both directions. The palindrome has two kinds. The first is `bab`, the center is one element, the other is `aaaa`, the center is `aa`, which is two elements.



```
public String longestPalindrome(String s) {
    if (s == null || s.length() == 0) {
        return "";
    }
    int start = 0;
    int end = 0;
    
    for (int i = 0; i < s.length(); i++) {
        int oneElementCenter = chckLongestPalindromicStringAt(i,i,s);
        int twoElementCneter = chckLongestPalindromicStringAt(i, i+1,s);
        
        int len = Math.max( twoElementCneter, oneElementCenter);
        if (len > end - start) {
            end = i + len / 2;
            start = i - (len - 1) / 2;
        }
    }
    
    return s.substring(start, end + 1);
}

private int chckLongestPalindromicStringAt(int left,int right, String s) {
    int l = left;
    int r = right;
    while (l >= 0 && r < s.length() && s.charAt(l) == s.charAt(r)) {
       
        l--;
        r++;
        
    }
    return r - l - 1;
} 
```
