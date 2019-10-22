## leetcode 322 零钱兑换
### 思路
硬币兑换是个动态规划问题
每次缺少某个硬币时所需要的最少个数来算

### 代码实现
```java
class Solution {
    public int coinChange(int[] coins, int amount) {
        int dp[] = new int[amount+1];;
        Arrays.fill(dp, amount+1);  
        dp[0] = 0;
        for (int i = 1; i < amount+1; i++){
            for (int j = 0; j < coins.length; j++){
                if(coins[j] <= i){
                    dp[i] = Math.min(dp[i] ,dp[i - coins[j]] + 1);
                }
            }
        }
        return dp[amount] > amount? -1 : dp[amount];
    }
}
```
