```java
class Solution {
    /**
    2
    3 4
    6 5 7
    4 1 8 3
    */
    public int minimumTotal(List<List<Integer>> triangle) {
        //行数
        int m = triangle.size();
        //列数
        int n = triangle.get(0).size();
        int[][] dp = new int[m][m];
        dp[0][0] = triangle.get(0).get(0);
        for (int j = 1; j < m; j++ ) {
            int k = triangle.get(j).size();
            for (int i = 1; i < k-1; i++) {
                dp[j][i] = Math.min(dp[j-1][i-1], dp[j-1][i])+triangle.get(j).get(i);
            }
            //边界条件
            dp[j][0] = dp[j-1][0]+triangle.get(j).get(0);
            dp[j][k-1] = dp[j-1][k-2] + triangle.get(j).get(k-1);
        }

        //遍历最后一行
        int ans = dp[m-1][0];
        for (int i = 1; i<m; i++) {
            ans = Math.min(dp[m-1][i], ans);
        }
        return ans;
    }
}
```

