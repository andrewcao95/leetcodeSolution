## Solution
这题字符串可以可以为空串，t为空串加1
程序依然正常运行
```java
class Solution {
    public char findTheDifference(String s, String t) {
        char res = t.charAt(t.length() - 1);
        for (int i = 0; i < s.length(); i++) {
            res ^= s.charAt(i) ^ t.charAt(i);
        }
        return res;
    }
}
```