### O(N2) time and constant space

A palindrome mirrors around its center. So a palindrome can be expanded around its center, and there are only 2n-1 centers.
We take every letter and every space between letters, try to expand a palindrome around it.
```
public String longestPalindrome(String s) {
    int l = s.length();
    int start = 0, end = 0;
    for (int i = 0; i < l; i++) {
        int len1 = expendAroundCenter(s, i, i);
        int len2 = expendAroundCenter(s, i, i + 1);
        int len = Math.max(len1, len2);
        if (len > end - start) {
            start = i - (len - 1) / 2;
            end =  i + len / 2;
        }
    }
    return s.substring(start, end + 1);
}

private int expendAroundCenter(String s, int left, int right) {
    int L = left, R = right;
    while (L >= 0 && R < s.length() && s.charAt(L) == s.charAt(R)) {
        L--;
        R++;
    }
    return R - L - 1;
}
```

There's even a linear time algorithm called [Manacher's](http://articles.leetcode.com/2011/11/longest-palindromic-substring-part-ii.html) algorithm.
[中文](http://www.felix021.com/blog/read.php?2040)
