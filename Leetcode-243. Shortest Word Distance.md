## Solution 1
- Time: O(n^2)
- Space: O(1)

暴力求解法，不推荐
```java
public class Solution {
    public static int test(String[] words, String word1, String word2) {
        int res = words.length;
        for (int i = 0; i < words.length; i++) {
            if (words[i].equals(word1)) {
                for (int j = 0; j < words.length; j++) {
                    if (words[j].equals(word2)) {
                        res = Math.min(res, Math.abs(i - j));
                    }
                }
            }
        }
        return res;
    }
}
```

## Solution 2
- Time: O(n)
- Space: O(1)

优化策略，使用index坐标来记录
```java
public class Solution {
    public static int test2(String[] words, String word1, String word2) {
            int res = words.length;
            int a = -1;
            int b = -1;
            for (int i = 0; i < words.length; i++) {
                if (words[i].equals(word1)) {
                    a = i;
                } else if (words[i].equals(word2)) {
                    b = i;
                }
            }
            if (a != -1 && b != -1) {
                res = Math.min(res, Math.abs(a - b));
            }
            return res;
    }
}
```
