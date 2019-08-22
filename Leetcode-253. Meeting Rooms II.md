## Solution
扫描线思想

先将各个时间段的start和end分别进行排序，然后进行扫描线判断


```
[     ] 
    [    ]
        [    ]
               [      ]
```

```java
public class Solution {
    public static int minMeetingRooms(Interval[] intervals) {
        int[] starts = new int[intervals.length];
        int[] ends = new int[intervals.length];
        for (int i = 0; i < intervals.length; i++) {
            starts[i] = intervals[i].start;
            ends[i] = intervals[i].end;
            //starts[i] = intervals[i][0];
            //ends[i] = intervals[i][1]; 
        }
        Arrays.sort(starts);
        Arrays.sort(ends);
        int res = 0;
        int end = 0;
        for (int i = 0; i < intervals.length; i++) {
            if (starts[i] < ends[end]) { //扫描线判断
                res++;
            } else {
                end++;
            }
        }
        return res;
    }
}

```
