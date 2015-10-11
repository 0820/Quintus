##@1
O(nklogk) time, k is the number of lists, n is the length of each list.

O(k) space due to heap
```
static Comparator<ListNode> cmp = new Comparator<ListNode>() {
    public int compare(ListNode left, ListNode right) {
        return left.val - right.val;
    }
};

public ListNode mergeKLists(ListNode[] lists) {
    ListNode root = new ListNode(0);
    if (lists == null || lists.length == 0)
        return null;

    Queue<ListNode> queue = new PriorityQueue<ListNode>(lists.length, cmp);
    for (ListNode list : lists) {
        if (list != null)
            queue.add(list);
    }

    ListNode current = root;
    while (!queue.isEmpty()) {
        current.next = queue.poll();
        current = current.next;
        if (current.next != null)
            queue.add(current.next);
    }

    current.next = null;
    return root.next;
}
```

##@2
Divide and conquer, O(nklogk) time, O(1) space

Works like merge sort, merge two lists at a time
