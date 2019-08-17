## Solution
facebook 面经的常考题
采用回溯算法实现，回溯算法的基本形式是“递归+循环”，正因为循环中嵌套着递归，递归中包含循环，这才使得回溯比一般的递归和单纯的循环更难理解，其实我们熟悉了它的基本形式，就会觉得这样的算法难度也不是很大。原数组中的每个元素有两种状态：存在和不存在。

- 外层循环逐一往中间集合 temp 中加入元素 nums[i]，使这个元素处于存在状态
- 开始递归，递归中携带加入新元素的 temp，并且下一次循环的起始是 i 元素的下一个，因而递归中更新 i 值为 i + 1
- 将这个从中间集合 temp 中移除，使该元素处于不存在状态

```java
class Solution {
    public List<List<Integer>> subsets(int[] nums) {
        List<List<Integer>> res = new ArrayList<List<Integer>>();
        List<Integer> temp = new ArrayList<Integer>();
        dfs(res, temp, nums, 0);
        return res;
    }
    
    public void dfs(List<List<Integer>> res, List<Integer> temp, int[] nums, int j) {
        res.add(new ArrayList<Integer>(temp));
        for (int i = j; i < nums.length; i++) {
            temp.add(nums[i]); //① 加入 nums[i]
            dfs(res, temp, nums, i + 1); //② 递归
            temp.remove(temp.size() - 1); //③ 移除 nums[i]
        }
    }
}

```