1. Implement a function to check if a tree is balanced.

This code runs in O(n) time and O(h) space.

```
public static int checkHeight(TreeNode root) {
  if (root == null) {
    return 0; // Height of 0
  }

  /* Check if left is balanced */
  int leftHeight = checkHeight(root.left);
  if (leftHeight == -1) {
    return -1; // Not balanced
  }
  /* Check if right is balance */
  int rightHeight = checkHeight(root.right);
  if (rightHeight == -1) {
    return -1; // Not balanced
  }

  /* Check if current node is balance */
  int heightDiff = leftHeight - rightHeight;
  if (Math.abs(heightDiff) > 1) {
    return -1;
  } else {
    /* Return height */
    return Math.max(leftHeight, rightHeight) + 1;
  }
}

public static boolean isBalanced(TreeNode root) {
  if (checkHeight(root) == -1) {
    return  false;
  } else {
    return  true;
  }
}
```
