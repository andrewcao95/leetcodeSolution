## Solution 1
```java
class Solution {
    public int addDigits(int num) {
        if (num == 0) {
            return 0;
        }
        while (num / 10 != 0) {
            num = num / 10 + num % 10;
        }
        return num;
    }
}
```

```java
class Solution {
    public int addDigits(int num) {
        if (num == 0) {
            return 0;
        }
        
        int sum = 0;
        while (num != 0) {
            sum += num % 10;
            num /= 10;
        }
        
        if (sum >= 10) {
            return addDigits(sum);
        } else {
            return sum;
        }
    }
}
```

## Solution 2
Follow up:
Could you do it without any loop/recursion in O(1) runtime?

```
1   1
2   2
3   3
4   4
5   5
6   6
7   7
8   8
9   9
10  1
11  2
12  3
13  4
14  5
15  6
16  7
17  8 
18  9
19  1
20  2
```

```java
class Solution {
    public int addDigits(int num) {
        return (num - 1) % 9 + 1;
    }
}
```