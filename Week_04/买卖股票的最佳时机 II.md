# 买卖股票的最佳时机 II

<https://leetcode-cn.com/problems/best-time-to-buy-and-sell-stock-ii/>

## 代码

```java
class Solution {
    public int maxProfit(int[] prices) {
        int max = 0;
        for (int i = 1; i < prices.length; i++) {
            max += Math.max(0, prices[i] - prices[i-1]);
        }
        return max;
    }
}
```