### 思路
双指针，只要不一样进一，然后交换

### 代码

```java
class Solution {
    public int removeDuplicates(int[] nums) {
        if (nums.length <= 1){
            return nums.length;
        }
        int len = nums.length;
        int j = 0;
        for ( int i = 1; i< nums.length; i++){
            if(nums[i] == nums[i-1]){
                len--;
            } else{
                j++;
                nums[j] = nums[i];
                
            }
        }
        return len;
    }
}
```