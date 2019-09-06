## Solution
思路很简单，
设置一个index指针，一次for遍历，将非0的值与index的值进行交换，交换后index++

这样可以保证在顺序一致的情况下将0往后面压

```java
class Solution {
    public void moveZeroes(int[] nums) {
        if (nums == null || nums.length == 0) {
            return;
        }
        int index = 0;
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] != 0) {
                int temp = nums[i];
                nums[i] = nums[index];
                nums[index]  = temp;
                index++;
            }
        }
    }
}
```