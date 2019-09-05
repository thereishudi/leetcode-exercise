

## 代码实现
```java
class Solution {
    public int maxArea(int[] height) {
        int start = 0;
        int end = height.length-1;
        int area = Math.min(height[start],height[end])*(end-start);
        while (start<end){
            int temparea = Math.min(height[start],height[end])*(end-start);
            area = temparea>area? temparea:area;
            if(height[start] > height[end]){
                end--;
            } else {
                start++;
            }
        }
        return area;
    }
}
```