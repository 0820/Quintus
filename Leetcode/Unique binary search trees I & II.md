#I
```
public int numTrees(int n) {
  // base case
  if (n == 0) return 0;

  // dp(i) represents the no. of unique BSTs till i
  // dp(0) = 1, means there's a null node
  int[] dp = new int[n + 1]; dp[0] = 1;

  for (int i = 1; i <= n; i++)
      // use j as root
      for (int j = 1; j <= i; j++)
          dp[i] += dp[j - 1] * dp[i - j];

  return dp[n];
}
```

#II
```
public List<TreeNode> generateTrees(int n) {
    return gT(1, n);
}

public List<TreeNode> gT(int start, int end) {
    List<TreeNode> res = new ArrayList<>();
    if (start > end) {
        res.add(null);
        return res;
    }
    
    for (int i = start; i <= end; i++) {
        List<TreeNode> l = gT(start, i - 1);
        List<TreeNode> r = gT(i + 1, end);
        for (TreeNode left : l) {
            for (TreeNode right : r) {
                TreeNode node = new TreeNode(i);
                node.left = left;
                node.right = right;
                res.add(node);
            }
        }
    }
    return res;
}
```
