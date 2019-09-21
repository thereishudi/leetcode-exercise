

### 代码

```java
class Solution {
    public int maxProfit(int[] prices) {
        if(prices==null || prices.length == 0){
            return 0;
        }
        int minnum = prices[0];
        int maxDiff = 0;
        for(int i = 0; i < prices.length; i++){
            minnum = minnum > prices[i]? prices[i]:minnum;
            maxDiff = prices[i]-minnum>maxDiff? prices[i]-minnum:maxDiff;
        }
        return maxDiff;
    }
}
```