## Solution

```java
class Solution {
    public int calculate(String s) {
        if (s == null || s.length() == 0) return 0;

        Stack<Integer> stack = new Stack<>();
        int res = 0;
        int sign = 1;
        for (int index = 0; index < s.length(); index++) {
            if (Character.isDigit(s.charAt(index))) {
                int num = s.charAt(index) - '0';
                while (index + 1 < s.length() && Character.isDigit(s.charAt(index + 1))) {
                    num = num * 10 + s.charAt(index + 1) - '0';
                    index++;
                }
                res += num * sign;
            } else if (s.charAt(index) == '+') {
                sign = 1; 
            } else if (s.charAt(index) == '-') {
                sign = -1;
            } else if (s.charAt(index) == '(') {
                stack.push(res);
                stack.push(sign);
                res = 0;
                sign = 1;  
            } else if (s.charAt(index) == ')') {
                res = res * stack.pop() + stack.pop();
            }
        }
        return res;
    }
}
```