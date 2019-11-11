## 暴力法
- Time:(O^2)

```java
class Solution {
    public int[] dailyTemperatures(int[] T) {
        int[] res = new int[T.length];
        if (T == null || T.length == 0)  {
            return res;
        }
        
        for (int i = 0; i < T.length; i++) {
            for (int j = i + 1; j < T.length; j++) {
                if (T[j] > T[i]) {
                    res[i] = j - i;
                    break;
                }
            }
        }
        return res;
    }
}
```

## 优化方法： 栈辅助
```java
//找出数组中大于当前元素的第一个元素，到当前元素的距离
//递减栈，当前元素与栈中元素比较，小则入栈，大则出栈并将二者之间的下标差值为出栈元素的结果值，并继续比较下一个栈顶元素
//如果栈为空，直接入栈(表示前面元素都找到了比自己大的值)

 class Solution {
    public int[] dailyTemperatures(int[] T) {
        Stack<Integer> stack = new Stack<>();
        int[] res = new int[T.length];
        for(int i = 0; i < T.length; ++i){
            while(!stack.isEmpty() && T[i] > T[stack.peek()]){
                int temp = stack.pop();
                res[temp] = i - temp;
            }
            stack.push(i);
        }
        return res;
    }
}
```

