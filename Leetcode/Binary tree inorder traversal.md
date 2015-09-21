```
public List<Integer> inorderTraversal(TreeNode root) {
   TreeNode node = root;
   List<Integer> list = new ArrayList<Integer>();
   while (node != null) {
       // POINT 1
       if (node.left == null) {
           list.add(node.val);
           node = node.right;
       } else {
           TreeNode temp = node.left;
           while (temp.right != null && temp.right != node) temp = temp.right;
           // POINT 2
           if (temp.right == node) {
               temp.right = null;
               list.add(node.val);
               node = node.right;
           // POINT 3
           } else {
               temp.right = node;
               node = node.left;
           }

       }
   }
   return list;
}
```
