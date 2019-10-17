## Solution
思路：非常简单的一道题，string的实现题，用正则把空格分隔开，然后判断长度，如果长度不为0，说明是有内容的，选最后一个取长度即可

time:O(n)
space:O(n)

```java
class Solution {
    public int lengthOfLastWord(String s) {
        String[] strings = s.split(" ");
        if (strings.length == 0) {
            return 0;
        } else {
            return strings[strings.length - 1].length();
        }
    }
}
```