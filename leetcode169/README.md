### ˼·
������������������ԣ�һ����������$n/2$�Ρ�
����������±���һ������Ϳ����ҳ����ִ�������$n/2$�Ǹ�����
ѡȡһ������������������ʱ����ǰ������֮ǰ���������ͬ���һ����ͬ���һ��
��������Ϊ0��ʱ��������Ϊ��ǰ�����������ֲ��Ҽ�����ֵ��Ϊ1.
### ����ʵ��
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