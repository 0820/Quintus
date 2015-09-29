#I
Typical backtracking, TLE

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
