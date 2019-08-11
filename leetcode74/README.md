#  leetcode 74
### 思路
这道题类似于全排列的实现，采用回溯法来解这个题。

### 代码实现
```
public List<List<Integer>> subsets(int[] nums) {
        int n=nums.length;
        ArrayList<List<Integer>> res = new ArrayList<List<Integer>>();
        ArrayList<Integer> temp = new ArrayList<Integer>();
        for(int i=0;i<=n;i++){
            subset(nums,res,temp,i,0,n);
        }
        return res;
    }
    public void subset(int[] nums,List<List<Integer>> res, List<Integer> temp, int m, int start,int end){
        if(m==0){
            res.add(new ArrayList<Integer>(temp));
            return;
        }
        else{
            for(int i=start;i+m<=end;i++){
                temp.add(nums[i]);
                subset(nums,res,temp,m-1,i+1,end);
                temp.remove(temp.size()-1);
            }
        }
    }
```