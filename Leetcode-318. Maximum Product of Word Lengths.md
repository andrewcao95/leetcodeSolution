## Solution
BitMap 位运算的使用
通过checker |= 1 << (chars[j] - 'a'); 将字符串进行位表示 32 * 8 = 256 压缩存储
```java
class Solution {
    public int maxProduct(String[] words) {
        if (words == null || words.length == 0) {
            return 0;
        }
        int n = words.length;
        int[] bits = new int[n];
        for (int i = 0; i < n; i++) {
            int checker = 0;
            char[] chars = words[i].toCharArray();   
            for (int j = 0; j < chars.length; j++) {
                checker |= 1 << (chars[j] - 'a');
            }
            bits[i] = checker;
        }
        
        int max = 0;
        for (int i = 0; i < n; i++) {
            for (int j = i + 1; j < n; j++) {
                if ((bits[i] & bits[j]) == 0) {
                    max = Math.max(max, words[i].length() * words[j].length());
                }
            }
        }
        return max;
    }
}
```