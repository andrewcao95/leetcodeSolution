## Solution

```java
class Solution {
    public String addBinary(String a, String b) {
        StringBuilder sb = new StringBuilder();
        int i = a.length() - 1;
        int j = b.length() - 1;
        int remainer = 0;
        
        while(i >= 0 || j >= 0) {
            int sum = remainer;
            if (i >= 0) {
                sum += a.charAt(i) - '0';
                i--;
            }
            if (j >= 0) {
                sum += b.charAt(j) - '0';
                j--;
            }
            sb.append(sum % 2);
            remainer = sum / 2;
        }
        if (remainer != 0) {
            sb.append(remainer);
        }
        return sb.reverse().toString();
    }
}

```