#II
Given an array of integers, every element appears three times except for one. Find that single one.

##@1 Linear time, No extra space
```
public int singleNumber(int[] A) {
    int n = A.length;
    int ones = 0, twos = 0, threes = 0;
    for (int i = 0; i < n; i++) {
        twos |= ones & A[i];
        ones ^= A[i];// 异或3次 和 异或 1次的结果是一样的
       //对于ones 和 twos 把出现了3次的位置设置为0 （取反之后1的位置为0）
        threes = ones & twos;
        ones &= ~threes;
        twos &= ~threes;
    }
    return ones;

}
```

#III
Given an array of numbers nums, in which exactly two elements appear only once and all the other elements appear exactly twice. Find the two elements that appear only once.

For example:

Given nums = [1, 2, 1, 3, 2, 5], return [3, 5].

##@1 HashSet solution
```
public int[] singleNumber(int[] nums) {
    Set<Integer> s = new HashSet<>();
    for (int num : nums) {
        if (!s.add(num))
            s.remove(num);
    }
    int[] r = new int[2];
    Iterator ite = s.iterator();
    int i = 0;
    while (ite.hasNext()) {
        r[i++] = (int)(ite.next());
        ite.remove();
    }
    return r;
}
```

##@2 Bit solution, O(1) space
```
int diff = 0;
for(int num: nums){
    diff ^= num;
}
diff = Integer.highestOneBit(diff);

int[] result = new int[2];
Arrays.fill(result, 0);
for (int num: nums) {
    if ((diff & num) == 0){
        result[0] ^= num;
    }
    else {
        result[1] ^= num;
    }
}
return result;
```
