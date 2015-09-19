#III

##Only one iteration, linear time, constant space

```
public int maxProfit(int[] prices) {
    int len = prices.length;
    if (len <= 1) return 0;
    int a, b, c, d;
    d = Math.max(prices[len-1], prices[len-2]);
    c = Math.max(prices[len-1] - prices[len-2], 0);
    b = d;
    a = c;
    for (int i = len - 3; i >= 0; i--) {
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

#IV

##@ 1

```
public int maxProfit(int k, int[] prices) {
        if (k > prices.length / 2) 
            return maxP(prices);
        int[][] hold = new int[prices.length][k+1];
        int[][] unhold = new int[prices.length][k+1];
        hold[0][0] = -prices[0];
        
        for (int i = 1; i < prices.length; i++) hold[i][0] = Math.max(hold[i-1][0],-prices[i]);
        for (int j = 1; j <= k; j++) hold[0][j] = -prices[0];
        for (int i = 1; i < prices.length; i++){
            for (int j = 1; j <= k; j++){
                hold[i][j] = Math.max(unhold[i-1][j] - prices[i], hold[i-1][j]);
                unhold[i][j] = Math.max(hold[i-1][j-1] + prices[i], unhold[i-1][j]);
            }
        }
        return Math.max(hold[prices.length-1][k], unhold[prices.length-1][k]);
    }
    public int maxP(int[] prices){
        int res = 0;
        for (int i = 1; i < prices.length; i++){
            if (prices[i] > prices[i - 1]){
                res += prices[i] - prices[i-1];
            }
        }
        return res;
    }
```
hold[i][j] means the maximum profit with at most j transaction for 0 to i-th day. hold means you have a stock in your hand.

unhold[i][j] means the maximum profit with at most j transaction for 0 to i-th day. unhold means you don't have a stock in your hand.


##@ 2

##O(nk) time, O(k) space
```
public int maxProfit(int k, int[] prices) {
        if (prices.length < 2) return 0;
        if (k > prices.length / 2) return maxProfit2(prices);
        
        int[] local = new int[k + 1];
        int[] global = new int[k + 1];
        
        for (int i = 1; i < prices.length ; i++) {
            int diff = prices[i] - prices[i - 1];
            for (int j = k; j > 0; j--) {
                local[j] = Math.max(global[j - 1] + Math.max(diff, 0), local[j] + diff);
                global[j] = Math.max(global[j], local[j]);
            }
        }
        
        return global[k];
    }
    
    
    public int maxProfit2(int[] prices) {
        int maxProfit = 0;
        
        for (int i = 1; i < prices.length; i++) {
            if (prices[i] > prices[i - 1]) {
                maxProfit += prices[i] - prices[i - 1];
            }
        }
        
        return maxProfit;
    }
```
