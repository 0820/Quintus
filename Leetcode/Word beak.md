#I

```
public boolean wordBreak(String s, Set<String> wordDict) {
    int l = s.length();
    boolean[] t = new boolean[l+1];
    t[0] = true;
    
    for (int i = 0; i < l; i++) {
        if(!t[i]) continue;
        
        for (String a : wordDict) {
            int c = a.length();
            int e = i + c;
            if (e > l) continue;
            if (t[e]) continue;
            if (s.substring(i,e).equals(a))
                t[e] = true;
        }
    }
    return t[l];
}
```

#II
##@1 DP & Backtracking

1. Similar to Word Break I, use DP to check if given string can be split to a group of words. 
If answer is no, simply return an empty list.

2. If answer is yes, then use backtracking to get all results. 
Basically, if we go to ith position, we need to iterate from 0 to i - 1. 
As long as the substring(0, i) can be split to words group, we need to recursively get the result. 
After that, concatenate each string in result with substring(i + 1, end). (Do not miss the space)

```
public List<String> wordBreak(String s, Set<String> wordDict) {
    if (s == null || "".equals(s)) return new ArrayList<String>();
    int[] dp = new int[s.length()];
    for (int i = 0; i < s.length(); i++) {
        if (wordDict.contains(s.substring(0, i + 1))) dp[i] = 1;
        else {
            for (int j = 0; j < i; j++) {
                if (dp[j] == 1 && wordDict.contains(s.substring(j + 1, i + 1))) {
                    dp[i] = 1;
                    break;
                }
            }
        }
    }
    if (dp[s.length() - 1] == 0) return new ArrayList<String>();
    return wordBreak(s, dp, s.length() - 1, wordDict);
}

private List<String> wordBreak(String s, int[] dp, int end, Set<String> wordDict) {
    List<String> result = new ArrayList<String>();
    for (int i = 0; i < end; i++) {
        if (dp[i] == 1 && wordDict.contains(s.substring(i + 1, end + 1))) {
            List<String> temp = wordBreak(s, dp, i, wordDict);
            for (String str : temp) result.add(str + " " + s.substring(i + 1, end + 1));
        }
    }
    if (wordDict.contains(s.substring(0, end + 1))) result.add(s.substring(0, end + 1));
    return result;
}
```

##@2

[Reference](http://www.cnblogs.com/springfor/p/3877056.html)
```
public boolean wordBreakcheck(String s, Set<String> dict) {
    if(s==null || s.length()==0)
      return true;
    boolean[] res = new boolean[s.length()+1];
    res[0] = true;
    for(int i=0;i<s.length();i++){
        StringBuilder str = new StringBuilder(s.substring(0,i+1));
        for(int j=0;j<=i;j++){
            if(res[j] && dict.contains(str.toString())){
                res[i+1] = true;
                break;
            }
            str.deleteCharAt(0);
        }
    }
    return res[s.length()];
}

public ArrayList<String> wordBreak(String s, Set<String> dict) {  
    ArrayList<String> res = new ArrayList<String>();  
    if(s==null || s.length()==0)  
        return res;
    if(wordBreakcheck(s,dict))
        helper(s,dict,0,"",res);  
    return res;  
}  
private void helper(String s, Set<String> dict, int start, String item, ArrayList<String> res){  
    if(start>=s.length()){  
        res.add(item);  
        return;  
    }
    
    StringBuilder str = new StringBuilder();  
    for(int i=start;i<s.length();i++){  
        str.append(s.charAt(i));  
        if(dict.contains(str.toString())){  
            String newItem = new String();  
            if(item.length()>0)
                newItem = item + " " + str.toString();
            else
                newItem = str.toString();
            helper(s,dict,i+1,newItem,res);  
        }  
    }  
}
```
