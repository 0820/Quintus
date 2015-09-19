##Only one iteration, linear time, constant space

```
public int maxProfit(int[] prices) {
    int len = prices.length;
    if(len <= 1) return 0;
    int a, b, c, d;
    d = Math.max(prices[len-1], prices[len-2]);
    c = Math.max(prices[len-1] - prices[len-2], 0);
    b = d;
    a = c;
    for(int i=len-3; i>=0; i--) {
        a = Math.max(b - prices[i], a);
        b = Math.max(prices[i] + c, b);
        c = Math.max(d - prices[i], c);
        d = Math.max(prices[i], d);
    }
    return a;
}
```

d is the value in the case when you have made a transaction before and you have a share at hand, that's basically the max from i to len.

c is the value in the case when you can make one transaction from days i to len. So c is updated only if you buy a share on that day and sell afterward.

b is the value in the case when you have a share at hand, and you can make one more transaction. So if you sell it on day i, it's prices[i] + c, otherwise it doesn't change.

a is the value in the case when you can make two transactions.
