## Solution
求最大面积，木桶原理，面积取决于最短的那条边
双指针模板
```
int res = 0
int l int r
while (l < r) {
    //处理
}
```

```java
class Solution {
    public int maxArea(int[] height) {
        int res = 0;
        int l = 0, r = height.length - 1;
        while (l < r) {
            res = Math.max(res, Math.min(height[l], height[r]) * (r - l));
            if (height[l] < height[r]) {
                l++;
            } else {
                r--;
            }
        }
        return res;
    } 
}
```