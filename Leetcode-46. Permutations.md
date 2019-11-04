## Solution 1
全排列
```java
class Solution {
    public List<List<Integer>> permute(int[] nums) {
        List<List<Integer>> res = new ArrayList<>();
        if (nums == null || nums.length == 0) {
            return res;
        }
        backtrack(res, new ArrayList<>(), nums);
        return res;
    }
    
    public void backtrack(List<List<Integer>> res, List<Integer> list, int[] nums) {
        if (list.size() == nums.length) {
            res.add(new ArrayList<>(list));
            return;
        }
        for (int i = 0; i < nums.length; i++) {
            if (list.contains(nums[i])) { //和时间复杂度有关系，利用tmp.isContains()时间复杂度为O(n)，访问数组某个元素时间复杂度为O(1)
                continue;
            }
            list.add(nums[i]);
            backtrack(res, list, nums);
            list.remove(list.size() - 1);
        }
    }
}
```