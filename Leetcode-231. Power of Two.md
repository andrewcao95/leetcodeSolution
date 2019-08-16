## Method
判断是否是2的幂，可以通过n & (n-1) == 0来判断

## Solution
```java
class Solution {
    public boolean isPowerOfTwo(int n) {
        if (n < 1) {
            return false;
        }
        return (n & (n - 1)) == 0;
    }
}
```