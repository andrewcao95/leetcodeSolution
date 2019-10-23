## Solution 1
- time:O(nlogn)
- space:O(1)
```java
class Solution {
    public int hIndex(int[] citations) {
        Arrays.sort(citations);
        int res = 0;
        while (res < citations.length && citations[citations.length - 1 - res] > res) {
            res++;
        }
        return res;
    }
}
```

## Solution 2
- time:O(n)
- spaceLO(n)
思想是使用技术排序将排序搜索的速度将time降到O(n)

![Xnip2019-10-23_11-53-13.jpg](http://pic-1255729225.cos.ap-shanghai.myqcloud.com/2019/10/24/de2ac7258213a.jpg)

```java
class Solution {
    public int hIndex(int[] citations) {
        int[] helper = new int[citations.length + 1];
        for (int i = 0; i < citations.length; i++) {
            helper[citations[i] <= citations.length ? citations[i] : citations.length] += 1;
        }
        int sum = 0;
        for (int i = citations.length; i > 0; i--) {
            sum += helper[i];
            if (sum >= i) {
                return i;
            }
        }
        return 0;
    }
}
```