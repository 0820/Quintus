#@1
```
if (head == null)
    return null;
ListNode fast = head;
ListNode slow = head;
ListNode prev = null; 
while (fast != null && fast.next != null) {
    fast = fast.next.next;
    prev = slow;
    slow = slow.next;
}

TreeNode root = new TreeNode(slow.val);
if (prev != null)
    prev.next = null;
else
    head = null;

root.left = sortedListToBST(head);
root.right = sortedListToBST(slow.next);
return root;
```

#@2

Much faster
```
if (head == null) {
    return null;
} else if (head.next == null) {
    return new TreeNode(head.val);
}
ListNode prev = null, cur = head, runner = head;
while (runner != null && runner.next != null) {
    prev = cur;
    cur = cur.next;
    runner = runner.next.next;
}
TreeNode root = new TreeNode(cur.val);
if (prev != null){
    prev.next = null;
    root.left = sortedListToBST(head);
}
root.right = sortedListToBST(cur.next);
return root;
```
