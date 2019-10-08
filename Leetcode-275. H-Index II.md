## Solution
```java
class Solution {
    public int hIndex(int[] citations) {
        int len = citations.length;
        int begin = 0;
        int end = len - 1;
        while (begin <= end) {
            int mid = (end - begin) / 2 + begin;
            if (citations[mid] == len - mid) {
                return len - mid;
            } else if (citations[mid] < len - mid) {
                begin = mid + 1;
            } else {
                end = mid - 1;
            }
        }
        return len - begin;
    }
}
```