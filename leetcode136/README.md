## leetcode134
### 思路
在考虑只遍历一遍并且不使用额外空间的条件下，这题可以用异或运算。因为一个数字异或自己本生为0。
而异或其他的数字不为零。这样最后留下的数字就是只出现了一次的数字。异或运算在Java中是 ^
### 代码
```
class Solution {
    public int singleNumber(int[] nums) {
        int ans = nums[0];
        if (nums.length > 1) {
           for (int i = 1; i < nums.length; i++) {
              ans = ans ^ nums[i];
           }
         }
         return ans;
    }
}
```