### 思路
这道题由于众数的特性，一个数超过了$n/2$次。
这样的情况下遍历一遍数组就可以找出出现次数超过$n/2$那个数。
选取一个计数器，遍历数组时，当前数字与之前标记数字相同便加一，不同便减一。
当计数器为0的时候标记数字为当前遍历到的数字并且计数器值置为1.
### 代码实现
```
class Solution {
    public int majorityElement(int[] nums) {
        int ans = nums[0];
        int count =1;
        if (nums.length == 0){
            return -1;
        }
        for (int i = 1; i< nums.length; i++){
            if (ans != nums[i]){
                count -- ;
                if (count == 0){
                    ans = nums[i];
                    count = 1;
                }
            }
            else {
                count++;
            }
        }
        return ans;
    }
}
```