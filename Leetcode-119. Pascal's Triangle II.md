## Solution
是118功能的截取，其他地方功能一致
```java
class Solution {
    public List<Integer> getRow(int rowIndex) {
        List<Integer> res = new ArrayList<>();
        if (rowIndex < 0) {
            return res;
        }
        for (int i = 0; i < rowIndex + 1; i++) {
            res.add(0, 1);
            for (int j = 1; j < res.size() - 1; j++) {
                res.set(j, res.get(j) + res.get(j + 1));
            }
        }
        return res;
    }
}
```