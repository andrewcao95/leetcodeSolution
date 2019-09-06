## Solution
质数从2开始
0和1都不是质数
创建一个boolean数组，遍历2~ sqrt(n)的值，将不能是质数的值置为true
```java
class Solution {
    public int countPrimes(int n) {
        if (n < 2) return 0;
        
        boolean[] notPrime = new boolean[n + 1];
        notPrime[0] = true;
        notPrime[1] = true;
        
        for (int i = 2; i < Math.sqrt(n); i++) {
            if (!notPrime[i]) {
                for (int j = 2; i * j < n; j++) {
                    notPrime[i * j] = true;
                }
            }
        }
        
        int count = 0;
        for (int i = 2; i < n; i++) {
            if (!notPrime[i]) {
                count++;
            }
        }
        return count;
    }
}
```