## Solution 1
使用Moore voting algorithm数学定理
思路是使用该公式，分别删除一对不相同的值，直到最后相同或者为空，即可得到
2 3 4 2 2 2 3 4 2 1
思路，把成对的元素删除


```java
class Solution {
    public int majorityElement(int[] nums) {
        int count = 0;
        int res = 0;
        for (int num : nums) {
            if (count == 0) {
                res = num;   
            }
            if (num != res) {
                count--;
            } else {
                count++;
            }
        }
        return res;
    }
}
```

## Solution 2
使用HashMap存储
```java
class Solution {
    public int majorityElement(int[] nums) {
        HashMap<Integer, Integer> map = new HashMap<>();
        
        for (int num : nums) {
            map.put(num, map.getOrDefault(num, 0) + 1);
        }
        for (Integer key : map.keySet()) {
            if (map.get(key) > nums.length / 2) {
                return key;
            }
        }
        return -1;
    }
}
```