## Solution
压栈匹配1

```java
class Solution {
    public String simplifyPath(String path) {
        Stack<String> stack = new Stack<>();
        String[] paths = path.split("/+");
        for (String s : paths) {
            if (s.equals("..")) {
                if (!stack.isEmpty()) {
                    stack.pop();
                }
            } else if (!s.equals(".") && !s.equals("")) {
                stack.push(s);
            }
        }
        String res = "";
        while (!stack.isEmpty()) {
            res = "/" + stack.pop() + res; //这里的字符串链接需要注意一下，将pop的值凡放在前面，与字符串读取的顺序的是一致的
        }
        
        return res.length() == 0 ? "/" : res;
    }
}
```