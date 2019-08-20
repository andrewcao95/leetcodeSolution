## Solution
思想简单，荷兰国旗问题
=0与start交换
=2与end交换
注意：与末尾交换时，交换回来的值可能并不是0， 所以不能将index前移
```java
class Solution {
    public void sortColors(int[] nums) {
        if (nums == null || nums.length == 0) return;
        
        int start = 0;
        int end = nums.length - 1;
        int index = 0;
        while (index <= end) {
            if (nums[index] == 0) {
                swap(nums, index++, start++);
            } else if (nums[index] == 1) {
                index++;
            } else {
                swap(nums, index, end--);
            }
        }
    }
    
    public void swap(int[] nums, int i, int j) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
}
```