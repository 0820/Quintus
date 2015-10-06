- Get Bit

This mehod shifts 1 over by i bits, creating a value that looks like 00010000. 
By performing an AND with num, we clear all bits other than the bit at bit i.
Finally, we compare that to 0. If that new value is not zero, then bit i must have a 1.
Otherwise, bit i is a 0.

```
boolean getBit(int num, int i) {
  return ((num & (1 << i)) != 0);
}
```

- Set Bit

SetBit shifts 1 over by i bits, creating a value like 00010000. By performing an OR with num,
only the value at bit i will change. All other bits of the mask are zero and will not affect num.

```
int setBit(int num, int i) {
  return num | (1 << i);
}
```

- Clear Bit

This method operates in almost the reverse of setBit. First, we create a number like 11101111
by creating the reverse of it (00010000) and nagating it. Then, we perform an AND with num.
This will clear the ith bit and leave the remainder unchanged.

```
int clearBit(int num, int i) {
  int mask = ~(1 << i);
  return num & mask;
}
```

To clear all bits from the most significant bit through i (inclusive), we create a mask with
1 at the ith bit (1 << i). Then, we subtract 1 from it, giving us a sequence of 0s followed by i 1s.
We then AND our number with this mask to leave just the last i bits.

```
int clearBitsMSBthroughI(int num, int i) {
  int mask = (1 << i) - 1;
  return num & mask;
}
```

To clear all bits from i through 0 (inclusive), we take a sequence of all 1s (which is -1)
and shift it over by 31 - i bits. By using the >>> operator, we shift the initial 1 as well that
indicates the sign bit. This give us a sequence of 1s followed by i 0 bits.

```
int clearBitsIthrough0(int num, int i) {
  int mask = ~(-1 >>> (31 - i));
  return num & mask;
}
```

- Update Bit

To set the ith bit to a value v, we first clear the bit at position i by using a mask that looks like
11101111. Then, we shift the intended value, v, left by i btis. This will create a number with bit i equal
to v and all other btis equal to 0. Finally, we OR these two numbers, updating the ith bit if v is 1 and
leaving it as 0 otherwise.

```
int updateBit(int num, int i, int v) {
  int mask = ~(1 << i);
  return (num & mask) | (v << i);
}
```
