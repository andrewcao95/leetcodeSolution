## Solution
```java
class Solution {
    public int titleToNumber(String s) {
        int res = 0;
        for (char ch : s.toCharArray()) {
            int num = ch - 'A' + 1;
            res = res * 26 + num;
        }
        return res;
    }
}
```