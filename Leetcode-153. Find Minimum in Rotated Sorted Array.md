## 直接遍历
- time:O(n)
```java
class Solution {
    public int findMin(int[] nums) {
        if (nums == null || nums.length == 0) return 0;
        int min = nums[0];
        for (int num : nums) {
            min = Math.min(min, num);
        }
        return min;
    }
}
```

## 二分法
- time:O(logn)
```java
class Solution {
    public int findMin(int[] nums) {
        if (nums == null || nums.length == 0) return 0;
        int left = 0;
        int right = nums.length - 1;
        while (left <= right) {
            int mid = (right - left) / 2 + left;
            if (nums[mid] >= nums[right]) {
                left = mid + 1;
            } else {
                right = mid;
            }
        }
        return nums[left - 1];
    }
}
```