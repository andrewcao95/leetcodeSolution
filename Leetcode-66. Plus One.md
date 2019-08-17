## Solution
三种情况都要考虑到
1 2 3  —— 1 2 4
1 2 9  —— 1 3 0
9 9 9  —— 1 0 0 0 


```java
class Solution {
    public int[] plusOne(int[] digits) {
        if (digits == null || digits.length == 0) {
            return digits;
        }
        
        for (int i = digits.length - 1; i >= 0; i--) {
            if (digits[i] < 9) {
                digits[i]++;
                return digits;
            } else {
                digits[i] = 0; 
            }
            
        }
        int[] res = new int[digits.length + 1];
        res[0] = 1;
        return res;
    }
}
```