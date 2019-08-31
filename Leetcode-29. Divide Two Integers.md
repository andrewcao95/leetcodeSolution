## Solution
参考篮子王

23 / 3
3 << 1 = 6
6 << 1 = 12()
12 << 1 = 24
--------
12 / 3
2） 3 << 1 = 6
4）6 << 1 = 12
-------------------
8 12 << 1 = 24




```java
class Solution {
    public int divide(int dividend, int divisor) {
        if (divisor == 0) return Integer.MAX_VALUE;
        if (dividend == Integer.MIN_VALUE) {
            if (divisor == -1) {
                return Integer.MAX_VALUE;
            } else if (divisor == 1) {
                return Integer.MIN_VALUE;
            }
        }
        
        long ldividend = (long) dividend;
        long ldivisor = (long) divisor;
        int sign = 1;
        if (ldividend < 0) {
            sign = -sign;
            ldividend = -ldividend;
        }
        if (ldivisor < 0) {
            sign = -sign;
            ldivisor = -ldivisor;
        }
        
        int res = 0;
        while (ldividend >= ldivisor) {
            int shift = 0;
            while (ldividend >= (ldivisor << shift)) {
                shift++;
            }
            res += (1 << (shift - 1));
            ldividend -= (ldivisor << (shift - 1));
        }
        return sign * res;
    }
}
```