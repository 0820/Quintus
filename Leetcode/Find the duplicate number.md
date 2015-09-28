O(n) time and O(1) space

The number array may be seen as a linked list and the value of node in the linked list is the index of next cell in array, 
since the value of integers in the array is between 1 and n

```
public int findDuplicate(int[] nums) {
    int fast, slow;

    fast = slow = nums[0];

    do {
        fast = nums[nums[fast]];
        slow = nums[slow];
    } while (fast != slow);

    slow = nums[0];
    while (fast != slow) {
        fast = nums[fast];
        slow = nums[slow];
    }

    return fast;
}
```
