## Solution
等概率抽样法，使用Random来进行

```java
class Solution {
    int[] nums;
    Random rmd;
    
    public Solution(int[] nums) {
        this.nums = nums;
        this.rmd = new Random();
    }
    
    public int pick(int target) {
        List<Integer> list = new ArrayList<>();
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] == target) {
                list.add(i);
            }
        }
        return list.get(rmd.nextInt(list.size())); // 注意这里是list坐标0，1，2，3，要从list中找到对应的原数组坐标再返回
    }
}

/**
 * Your Solution object will be instantiated and called as such:
 * Solution obj = new Solution(nums);
 * int param_1 = obj.pick(target);
 */
```