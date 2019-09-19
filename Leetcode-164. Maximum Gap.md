## Solution
遇到这类问题肯定先想到的是要给数组排序，但是题目要求是要线性的时间和空间，那么只能用桶排序或者基排序。这里我用桶排序Bucket Sort来做，首先找出数组的最大值和最小值，然后要确定每个桶的容量，即为 (最大值 - 最小值) / 个数 + 1，在确定桶的个数，即为 (最大值 - 最小值) / 桶的容量 + 1，然后需要在每个桶中找出局部最大值和最小值，而最大间距的两个数不会在同一个桶中，而是一个桶的最小值和另一个桶的最大值之间的间距，这是因为我们希望所有的数字能尽量平均分配到每个桶中，而不是都拥挤在一个桶中，这样保证了最大值和最小值一定不会在同一个桶中

```java
class Solution {
    public int maximumGap(int[] nums) {
        if (nums == null || nums.length < 2) return 0;
        
        int min = Integer.MAX_VALUE;
        int max = Integer.MIN_VALUE;
        for (int num: nums) {
            min = Math.min(min, num);
            max = Math.max(max, num);
        }
        int size = (max - min) / nums.length + 1;
        int bucketNum = (max - min) / size + 1;
        
        int[] bucketsMin = new int[bucketNum];
        int[] bucketsMax = new int[bucketNum];
        
        Arrays.fill(bucketsMin, Integer.MAX_VALUE);
        Arrays.fill(bucketsMax, Integer.MIN_VALUE);
        
        for (int num : nums) {
            int index = (num - min) / size;
            bucketsMin[index] = Math.min(bucketsMin[index], num);
            bucketsMax[index] = Math.max(bucketsMax[index], num);
        }
        
        int res = 0;
        int pre = 0;
        for (int i = 1; i < bucketNum; i++) {
            if (bucketsMin[i] == Integer.MAX_VALUE || bucketsMax[i] == Integer.MIN_VALUE) {
                continue;
            }
            res = Math.max(res, bucketsMin[i] - bucketsMax[pre]);
            pre = i;
        }
        return res;
    }
}
```