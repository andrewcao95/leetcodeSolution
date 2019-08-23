## Solution
二维矩阵，当每行是递增，每列是递增，但是穿起来不是递增的情况，可以使用暴力循环遍历来求解

```java
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        if (matrix == null || matrix.length == 0 || matrix[0] == null || matrix[0].length == 0) {
            return false;
        }    
        int row = 0;
        int col = matrix[0].length - 1;
        while (col >= 0 && row <= matrix.length - 1) {
            if (target == matrix[row][col]) {
                return true;
            } else if (target < matrix[row][col]) {
                col--;
            } else {
                row++;
            }
        }
        return false;
    }
}
```