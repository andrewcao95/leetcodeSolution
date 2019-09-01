## Solution
思路，while循环暴力求解不是我们想要的方法
我们的主要思路还是二分法
要考虑corner case
指数的奇偶、正负

对于奇偶
奇数的情况res*当前的num
res num power
1       2   7
1*2     2   6
1*2     4   3
1*2*4   4   2
1*2*4   16  1

=1*2*4（res） * 16(num)

对于正负的情况
负数可以通过 2^(-2) = 1 / 2^2

将2^(-2) -> 2^(2)
负数转正数，考虑corner case，当负数为最大时，MIN_VALUE = -27******2
而对于正数，MAX_VALUE= 27*****1 比负数小一个，所以当负数转正数的时候为了避免溢出，需要做处理

1 / (num * myPow(x, -(n + 1))); //指数+1，在值就要除去对应的值


```java
class Solution {
    public double myPow(double x, int n) {
        if (x == 1 || n == 0) return 1;
        if (n == 1) return x;
        if (n < 0) {
            return 1 / (x * myPow(x, -(n + 1)));
        }
        double res = 1;
        while (n > 1) {
            if (n % 2 == 1) {
                res *= x;
            }
            x *= x;
            n /= 2;
        }
        res *= x;
        return res;
    }
}
```