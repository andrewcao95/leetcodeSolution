开方问题一般有几种解法
- 暴力法（时间复杂度很高）
- 二分法（面试时最容易问到）

## Solution 1 暴力法
- time: O(n)
- space: O(1)
```java
class Solution {
  public boolean isPerfectSquare(int num) {
        for (int i = 1; i <= num; i++) {
            if (i * i == num) {
                return true;
            }
        }
        return false;
    }
}
```

## Solution 2 二分法
- time: O(logn)
- space: O(1)
```java
class Solution {
    public boolean isPerfectSquare(int num) {
        int low = 1;
        int high = num;
        while (low <= high) {
            long mid = (high - low) / 2 + low;
            if (mid * mid == num) {
                return true;
            } else if (mid * mid < num) {
                low = (int)mid + 1;
            } else {
                high = (int)mid - 1;
            }
        }
        return false;
    }
}
```

## Solution 3  x * x > m
- time: O(sqrt(n)) sqrt(n)比logn还要小
- space: O(1)
```java
class Solution { 
    public boolean isPerfectSquare(int num) {
        if (num == 1) return true;
        for (int i = 1; i <= num / i; i++) {
            if (i * i == num) {
                return true;
            }
        }
        return false;
    }
}
```