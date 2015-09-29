#I
Typical backtracking

##@1
```
public List<List<String>> partition(String s) {
    List<List<String>> res = new ArrayList<>();
    helper(s, 0, new ArrayList<String>(), res);
    return res;
}

public void helper(String s, int index, ArrayList<String> a, List<List<String>> r) {
    if (s == null) return;
    int l = s.length();
    if (index == l) {
        r.add(new ArrayList(a));
    }
    
    for (int i = index; i < l; i++) {
        if ( isPalindrome(s.substring(index, i + 1)) ) {
            a.add(s.substring(index, i+1));
            helper(s, index + 1, a, r);
            a.remove(a.size() - 1);
        }
    }
}

private boolean isPalindrome(String s) {
    int l = 0, r = s.length() - 1;
    while (l < r) {
        if (s.charAt(l) != s.charAt(r)) 
            return false;
        l++;
        r--;
    }
    return true;
}
```

##@2
```
public List<List<String>> partition(String s) {
    List<List<String>> res = new ArrayList<List<String>>();
    if (s.equals("")) {
        res.add(new ArrayList<String>());
        return res;
    }
    for (int i = 0; i < s.length(); i++) {
        if (isPalindrome(s, i + 1)) {
            for (List<String> list : partition(s.substring(i+1))) {
                list.add(0, s.substring(0, i + 1));
                res.add(list);
            }
        }
    }
    return res;
}

public boolean isPalindrome(String s, int n) {
    for (int i = 0; i < n / 2; i++) {
        if (s.charAt(i) != s.charAt(n - i - 1))
            return false;
    }
    return true;
}
```

#II

dp[i][j] means whether substring of s from i to j can form a Palindrome.

```
public int minCut(String s) {
    if (s == null || s.length() == 0) {
      return 0;
    }
    
    int n = s.length();
    
    // build the dp matrix to hold the palindrome information
    // dp[i][j] represents whether s[i] to s[j] can form a palindrome
    boolean[][] dp = buildMatrix(s, n);
    
    // res[i] represents the minimum cut needed
    // from s[0] to s[i]
    int[] res = new int[n];
    
    for (int j = 0; j < n; j++) {
      // by default we need j cut from s[0] to s[j]
      int cut = j;
    
      for (int i = 0; i <= j; i++) {
        if (dp[i][j]) {
          // s[i] to s[j] is a palindrome
          // try to update the cut with res[i - 1]
          cut = Math.min(cut, i == 0 ? 0 : res[i - 1] + 1);
        }
      }
    
      res[j] = cut;
    }
    
    return res[n - 1];
}
    
boolean[][] buildMatrix(String s, int n) {
    boolean[][] dp = new boolean[n][n];
    
    for (int i = n - 1; i >= 0; i--) {
      for (int j = i; j < n; j++) {
        if (s.charAt(i) == s.charAt(j) && (j - i <= 2 || dp[i + 1][j - 1])) {
          dp[i][j] = true;
        }
      }
    }
    
    return dp;
}
```
