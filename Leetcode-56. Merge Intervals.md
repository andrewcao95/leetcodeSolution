## Solution
扫描线算法来求解

- time:O(nlogn)
- space:O(n)

```java
class Solution {
    public int[][] merge(int[][] intervals) {
        if (intervals == null || intervals.length <= 1) {
            return intervals;
        }
        Arrays.sort(intervals, (a, b) -> a[0] - b[0]);
        int start = intervals[0][0];
        int end = intervals[0][1];
        List<int[]> res = new ArrayList<>();
        
        for (int[] interval : intervals) {
           if (interval[0] <= end) {
               end = Math.max(end, interval[1]);
           } else {
               res.add(new int[]{start, end});
               start = interval[0];
               end = interval[1];
           }
        }
        res.add(new int[]{start, end});
        
        return res.toArray(new int[res.size()][]);
    }
}
```