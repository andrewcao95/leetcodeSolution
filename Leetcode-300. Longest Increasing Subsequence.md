## Solution 1
使用耐心排序 + 二分查找的思路实现
思路：新开一个数组，不断的将原数组的值复制进去，当比原来的值小，就覆盖，当大于，就在旁边插入

可以实现：
time:O(logn)
space:O(n)

```java
class Solution {
    public int lengthOfLIS(int[] nums) {
        int[] tails = new int[nums.length];
        int res = 0;
        for (int num : nums) {
            int i = 0, j = res;
            while (i != j) {
                int mid = (i + j) / 2;
                if (tails[mid] < num) {
                    i = mid + 1;
                } else {
                    j = mid;
                }
            }
            tails[i] = num;
            if (i == res) res++;
        }
        return res;
    }
}
```


## Solution 2
DP的思路
可以实现
time:O(n^2)
space:O(n)