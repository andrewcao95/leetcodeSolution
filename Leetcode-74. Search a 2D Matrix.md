## Solution
矩阵的二分法
需要注意的是矩阵mid的值是通过value = matrix[mid / col][mid % col]来取的，这个要背
```java
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        if (matrix == null || matrix.length == 0 || matrix[0] == null || matrix[0].length == 0) {
            return false;
        }
        int row = matrix.length;
        int col = matrix[0].length;
        int begin = 0;
        int end = row c* col - 1;
        while (begin <= end) {
            int mid = (end - begin) / 2 + begin;
            int value = matrix[mid / col][mid % col]; //要背
            if (value == target) {
                return true;
            } else if (value < target) {
                begin = mid + 1;
            } else {
                end = mid - 1;
            }
        }
        return false;
    }
}
```