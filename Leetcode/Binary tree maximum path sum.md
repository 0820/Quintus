In each recursion update the max value with the sum of left, right and root value

But the recursive function itself should return only one child of the node

```
private int result = Integer.MIN_VALUE;
public int maxPathSum(TreeNode root) {
    dps(root);
    return result;
}

public int dps(TreeNode root) {
    if (root == null) return 0;
    int l = Math.max(dps(root.left), 0);
    int r = Math.max(dps(root.right), 0);
    
    result = Math.max(result, l + r + root.val);
    return Math.max(l, r) + root.val;
}
```
