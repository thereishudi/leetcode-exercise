
##  思路
在线处理的方法找到最大值

## 代码实现
``` java
class Solution {
    public int maxSubArray(int[] nums) {
        int sum = 0;
        int ans = nums[0];
        for (int i = 0; i<nums.length; i++){
            sum += nums[i];
            
            if(sum > ans){
                ans = sum;
            }
            
            if(sum < 0){
                sum = 0;
            }
        }
        return ans;
    }
}
```