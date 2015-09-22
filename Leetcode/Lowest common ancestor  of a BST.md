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
