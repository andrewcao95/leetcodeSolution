## Solution 1 递归
- time:O(2^n)
- space: O(n)
```java
class Solution {
    public int climbStairs(int n) {
        if (n <= 2) {
            return n;
        } else {
            return climbStairs(n - 1) + climbStairs(n - 2);
        }
    }
}
```

## Solution 2 迭代（动态规划法填表）
- time: O(n)
- space: O(n)

```java
class Solution {
    public int climbStairs(int n) {
        if (n <= 2) {
            return n;
        } else {
            int[] temp = new int[n];
            temp[0] = 1;
            temp[1]	= 2;
            for (int i = 2; i < n; i++) {
                temp[i] = temp[i - 1] + temp[i - 2]; 
            }
            return temp[n - 1];
        }
    }
}
```
## Solution 3 迭代
- time: O(n)
- space: O(1)

```java
class Solution {
    public int climbStairs(int n) {
        if (n <= 1) return 1;
        int oneStep = 1, twoStep = 1, res = 0;
        for (int i = 2; i <= n; i++) {
            res = oneStep + twoStep;
            twoStep = oneStep;
            oneStep = res;
        }
        return res;
    }
}
```