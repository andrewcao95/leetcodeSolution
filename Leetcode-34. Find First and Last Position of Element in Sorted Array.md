## Solution
思路：
target - 0.5
target + 0.5

567788888910 找8
由于left <= right之后的边界条件是

7 8 8 8 9 10
e s   e s

可以通过2次调用binarysearch来找到对应的区间



```java
class Solution {
    public int[] searchRange(int[] nums, int target) {
        int[] res = new int[] {-1, -1};
        if (nums == null || nums.length == 0) {
            return res;
        }
        int left = binarySearch(nums, target - 0.5);
        int right = binarySearch(nums, target + 0.5);
        if (right - left == 0) {
            return res;
        } 
        res[0] = left;
        res[1] = right - 1;
        return res;
    }
    
    public int binarySearch(int[] nums, double target) {
        int start = 0;
        int end = nums.length - 1;
        while (start <= end) {
            int mid = (end - start) / 2 + start;
            if (nums[mid] < target) {
                start = mid + 1;
            } else {
                end = mid - 1;
            }
        }
        return start;
    }
}
```