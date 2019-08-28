### 思路
因为每次两人都可以固定的取到四个，因此只要对4取余数，不为0就可以直接取到最后一块石头

### 代码
```
class Solution {
    public boolean canWinNim(int n) {
        n = n%4;
        if(n >0){
            return true;
        } else{
            return false;
        }
        
    }
}
```