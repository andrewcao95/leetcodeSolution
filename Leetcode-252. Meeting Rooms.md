## Solution
使用Arrays.sort() 中的lambda表达式

```java
public class Solution {
    public static boolean canAttendMeetings(Interval[] intervals) {
        Arrays.sort(intervals, (x, y) -> x.start - y.start);
        for (int i = 1; i < intervals.length; i++) {
            if (intervals[i - 1].end > intervals[i].start) {
                return false;
            }
        }
        return true;
    }
}

```

```java
class Solution {
    public boolean canAttendMeetings(int[][] intervals) {
        Arrays.sort(intervals, (x, y) -> x[0] - y[0]);
        for(int i = 1; i < intervals.length; i++) {
            if(intervals[i - 1][1] > intervals[i][0])
            return false;
        }
        return true;
    }
}
```