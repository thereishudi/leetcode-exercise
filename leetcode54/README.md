### leetcode54
思路按层打印数数组

### 代码实现
```java
class Solution {
    public List<Integer> spiralOrder(int[][] matrix) {
        List<Integer> ans = new ArrayList<Integer>();
        if(matrix.length <=0 ){
            return ans;
        }
        int rowstart = 0,rowend = matrix.length-1, colstart = 0, colend = matrix[0].length-1;
        while(rowstart <= rowend && colstart <= colend){
            if(!(rowstart <= rowend && colstart <= colend)){
                break;
            }
            for (int i = colstart; i<=colend; i++){
                ans.add(matrix[rowstart][i]);
            }
            rowstart++;
            if(!(rowstart <= rowend && colstart <= colend)){
                break;
            }
            for (int i = rowstart; i<=rowend; i++){
                ans.add(matrix[i][colend]);
            }
            if(!(rowstart <= rowend && colstart <= colend)){
                break;
            }
            colend--;
            for (int i = colend; i>=colstart; i--){
                ans.add(matrix[rowend][i]);
            }
            rowend--;
            if(!(rowstart <= rowend && colstart <= colend)){
                break;
            }
            for (int i = rowend; i>=rowstart; i--){
                ans.add(matrix[i][colstart]);
            }
            colstart++;
        }
        return ans;
        
    }
}
```