## leetcode134
### ˼·
�ڿ���ֻ����һ�鲢�Ҳ�ʹ�ö���ռ�������£����������������㡣��Ϊһ����������Լ�����Ϊ0��
��������������ֲ�Ϊ�㡣����������µ����־���ֻ������һ�ε����֡����������Java���� ^
### ����
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