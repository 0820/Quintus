#III

@1 HashSet solution
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

@2 Bit solution, O(1) space
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
