## Solution
思路：
对于字符串来说，这种是丰巢洋葱式
所以我们需要一层一层的剥开
通过题意知道可以分为
数字
[    
]
字母
所以可以逐一进行讨论

例如：12[ac]
对于字母的处理，就直接进行逐一拼接成字符串即可
对于数字的处理，通过读取数字，将数字压入到一个存放数字的栈
对于[的处理，将当前的res压入res栈，并且将res=“”保证[之后的字符串保存不受影响
对于]的处理，将当前res字符串和已经被压入栈中的字符串进行拼接，再将拼接后的字符串作为res值


```java
class Solution {
    public String decodeString(String s) {
        if (s == null || s.length() == 0) {
            return s;
        }
        
        Stack<Integer> numStack = new Stack<>();
        Stack<String> resStack = new Stack<>();
        String res = "";
        int idx = 0;
        while (idx < s.length()) {
            if (Character.isDigit(s.charAt(idx))) {
                int num = 0;
                while (Character.isDigit(s.charAt(idx))) {
                    num = num * 10 + s.charAt(idx) - '0';
                    idx++;
                }
                numStack.push(num);
            } else if (s.charAt(idx) == '[') {
                resStack.push(res);
                res = "";
                idx++;
            } else if (s.charAt(idx) == ']') {
                StringBuilder temp = new StringBuilder(resStack.pop());
                int time = numStack.pop();
                for (int i = 0; i < time; i++) {
                    temp.append(res);
                }
                res = temp.toString();
                idx++;
            } else {
                res +=  s.charAt(idx++);
            }
        }
        return res;
    }
}
```