## Solution
```java
class Solution {
    int[] nums;
    Random rmd;
    
    public Solution(int[] nums) {
        this.nums = nums;
        this.rmd = new Random();
    }
    
    /** Resets the array to its original configuration and return it. */
    public int[] reset() {
        return nums;
    }
    
    /** Returns a random shuffling of the array. */
    public int[] shuffle() {
        if (nums == null) return nums;
        int[] clone = nums.clone();
        for (int i = 1; i < clone.length; i++) {
            int random = rmd.nextInt(i + 1);
            swap(clone, i, random);
        }
        return clone;
    }
    
    public void swap(int[] nums, int i, int j) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
}

/**
 * Your Solution object will be instantiated and called as such:
 * Solution obj = new Solution(nums);
 * int[] param_1 = obj.reset();
 * int[] param_2 = obj.shuffle();
 */
```