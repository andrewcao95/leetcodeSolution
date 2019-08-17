## Solution 1
使用n&(n-1)进行位运算，逐一进行去1操作，并统计

```java
public class Solution {
    // you need to treat n as an unsigned value
    public int hammingWeight(int n) {
        int res = 0;
        while (n != 0) {
            n = n & (n - 1);
            res++;
        }
        return res;
    }
}
```

## Solution 2
使用n & 1 统计末尾的1的个数

```java
public class Solution {
    // you need to treat n as an unsigned value
    public int hammingWeight(int n) {
        int res = 0;
        for (int i = 0; i < 32; i++) {
            res += (n & 1);
            n >>= 1;
        }
        return res;
    }
}
```
