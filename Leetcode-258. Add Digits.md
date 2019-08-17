## Solution 1
```java
class Solution {
    public int addDigits(int num) {
        if (num == 0) {
            return 0;
        }
        while (num / 10 != 0) {
            num = num / 10 + num % 10;
        }
        return num;
    }
}
```

## Solution 2
Follow up:
Could you do it without any loop/recursion in O(1) runtime?