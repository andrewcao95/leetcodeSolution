## Solution 二分法
- time: O(logn)
- space: O(1)
```java
class Solution {
    public int mySqrt(int x) {
        if (x < 1) {
            return 0;
        }
        int low = 1;
        int high = x;
        while (low <= high) {
            long mid = (high - low) / 2 + low;
            if (mid * mid == x) {
                return (int) mid;
            } else if (mid * mid < x) {
                low = (int) mid + 1;
            } else if (mid * mid > x) {
                high = (int) mid - 1;
            }
        }
        return (int) high;
    }
}
```
## Solution 牛顿法
- time: 不知道
- space: O(1)
```java
class Solution {
    public int mySqrt(int x) {
        long res = x;
        while (res * res > x) {
            res = (res + x / res) / 2;
        }
        return (int) res;
    }
}
```