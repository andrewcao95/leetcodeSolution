## Solution
```java
class Solution {
    public String longestCommonPrefix(String[] strs) {
        if (strs == null || strs.length == 0) return "";
        
        for (int i = 0; i < strs[0].length(); i++) {
            char c = strs[0].charAt(i);
            for (int j = 1; j < strs.length; j++) {
                if (i == strs[j].length() || strs[j].charAt(i) != c) { //这里第一个条件是当第一个字符串的比较指针已经到达后面这个字符的末尾的时候，说明比较已经结束了
                    return strs[0].substring(0, i);
                }
            }
        }
        return strs[0];
    }
}
```