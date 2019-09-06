## Solution
```java
//朴素解法
class Solution {
    public boolean isUgly(int num) {
        if (num < 1) return false;
        
        while (num % 2 == 0) {
            num /= 2;
        }
        while (num % 3 == 0) {
            num /= 3;
        }
        while (num % 5 == 0) {
            num /= 5;
        } 
        if (num == 1) {
            return true;
        } else {
            return false;
        }       
    }
}

//优化代码
class Solution {
    public boolean isUgly(int num) {
        for (int i = 2; i < 6 && num > 0; i++) {
            while(num % i == 0) num /= i;
        }
        return num == 1;
    }
}
```