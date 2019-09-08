## Solution
由于数组有序
判断后一个值与前一个值是否相同
如果不相同，则将后一个值赋值到前一个值进行覆盖，并且通过index指针来控制新的数组的取值范围

- time: O(n)
- space: O(1)
```java
class Solution {
    public int removeDuplicates(int[] nums) {
        if (nums == null || nums.length == 0) {
            return 0;
        }
    
        int index = 1;
        for (int i = 1; i < nums.length; i++) {
            if (nums[i-1] != nums[i]) {
                nums[index++] = nums[i];
            }
        }
        return index;
    }
}
```