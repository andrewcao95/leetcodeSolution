## Solution
思想：
通过trim（）去除字符串前后空格
用sign表示正负
并且要考虑超过表达范围的情况处理

```java
class Solution {
    public int myAtoi(String str) {
        str = str.trim();
        if (str == null || str.length() == 0) {
            return 0;
        }

        int sign = 1;
        long res = 0;
        int start = 0;
        char firstChar = str.charAt(0);
        if (firstChar == '+') {
            start++;
        } else if (firstChar == '-') {
            sign = -1;
            start++;
        } 
        
        for (int i = start; i < str.length(); i++) {
            if (!Character.isDigit(str.charAt(i))) {
                return (int)res * sign;
            }
            res = res * 10 + str.charAt(i) - '0';
            if (sign == 1 && res > Integer.MAX_VALUE) return Integer.MAX_VALUE;
            if (sign == -1 && res > Integer.MAX_VALUE) return Integer.MIN_VALUE; 
        }
        return (int)res * sign;
    }
}
```