## Solution 1
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

## Solution 2
区间思想
The basic idea is to compare current end time with next start time, if next start time is smaller than current end time, then there is a collapse. In order to achieve this approach, we need to

Seperate start time and end time into different arrays and sort them in ascending order.
For each end time, compare it with next start time. We use j to mark start time and i to mark end time. When collapse appears, record start time and end time, and move j to next end time(which is i++) as the new start.
Since this approach will miss the last stat time, add the last time section with start time j and the final end time.

```java
public int[][] merge(int[][] intervals) {
    if(intervals == null || intervals.length == 0){
        return new int[0][];
    }
    // seperate start and end 
    int[] start = new int[intervals.length];
    int[] end = new int[intervals.length];
    List<int[]> res = new LinkedList<>();
    for(int i = 0; i < intervals.length; i++){
        start[i] = intervals[i][0];
        end[i] = intervals[i][1];
    }
    
    // sort start[] end[] respectively
    Arrays.sort(start);
    Arrays.sort(end);
    
    int j = 0; // start time
    for(int i = 0; i < intervals.length - 1; i++) { // iterate end time
        if(start[i + 1] > end[i]) { // when collapse appears
            res.add(new int[] {start[j], end[i]}); // record
            j = i + 1; // move previous start time 
        }    
    }
    res.add(new int[] {start[j], end[intervals.length - 1]}); // add last one
    return res.toArray(new int[res.size()][]);
}
```