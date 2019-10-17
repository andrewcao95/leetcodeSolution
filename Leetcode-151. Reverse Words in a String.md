## Solution
```java
class Solution {
    public String reverseWords(String s) {
        if (s == null || s.length() == 0) {
            return "";
        }
        String[] strings = s.trim().split("\\s+");
        StringBuilder sb = new StringBuilder();
        for (int i = strings.length - 1; i >= 0; i--) {
            sb.append(strings[i] + " ");
        }
        return sb.toString().trim();
    }
}
```