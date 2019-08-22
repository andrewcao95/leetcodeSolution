## Solution
使用Moore voting algorithm数学定理
思路是使用该公式，分别删除一对不相同的值，直到最后相同或者为空，即可得到
2 3 4 2 2 2 3 4 2 1


```java
class Solution {
    public int majorityElement(int[] nums) {
        int count = 0;
        int res = 0;
        for (int num : nums) {
            if (count == 0) {
                res = num;   
            }
            if (num != res) {
                count--;
            } else {
                count++;
            }
        }
        return res;
    }
}
```