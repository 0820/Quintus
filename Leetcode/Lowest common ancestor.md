#Lowest Common Ancestor of a BST
Recursive
```
int a = root.val;
if (p.val < a && q.val < a) return lowestCommonAncestor(root.left, p, q);
if (p.val > a && q.val > a) return lowestCommonAncestor(root.right, p, q);

return root;
```


Iterative
```
while (true) {
    if ((root.val-p.val) * (root.val-q.val) <= 0) return root;
    if (p.val < root.val)
        root = root.left;
    else
        root = root.right;
}
```

#Lowest Common Ancestor of a Binary Tree
```
public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
    return lca(root, p, q);
}
public TreeNode lca(TreeNode r, TreeNode p, TreeNode q) {
    if (r == null) return null;
    if (p == r || q == r) return r;
    TreeNode left = lca(r.left, p, q);
    TreeNode right = lca(r.right, p, q);
    
    if (left != null && right != null) return r;
    return left != null ? left : right;
}
```
