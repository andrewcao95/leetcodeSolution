## Solution
二分法的分段操作


4 5 6 7 0 1 2 3

1. nums[left] target nums[mid] 4 ~ mid ~ 7
2. nums[mid] target nums[right] 0 ~ mid ~ 3

由于4 5 6 7和0 1 2 3这两段是有序的
So, the mid value will both in frist segment and the second segment
进行分别讨论
nums[left] <= nums[mid] 和nums[mid] >= nums[right]


```java
class Solution {
    public int search(int[] nums, int target) {
        if (nums == null || nums.length == 0) {
            return -1;
        }
        int left = 0;
        int right = nums.length - 1;
        while (left <= right) {
            int mid = (right - left) / 2 + left;
            if (nums[mid] == target) {
                return mid;
            }
            if (nums[left] <= nums[mid]) {
                if (target >= nums[left] && target < nums[mid]) {
                    right = mid - 1;
                } else {
                    left = mid + 1;
                }
            } else if (nums[mid] <= nums[right]) {
                if (target > nums[mid] && target <= nums[right]) {
                    left = mid + 1;
                } else {
                    right = mid - 1;
                }
            }
        }
        return -1;
    }
}
```