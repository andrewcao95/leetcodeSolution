## Solution
```java
public class Solution{
    public static boolean isStrobogrammatic(String str) {
        HashMap<Character, Character> map = new HashMap<>();
        map.put('0', '0');
        map.put('1', '1');
        map.put('6', '9');
        map.put('8', '8');
        map.put('9', '6');
        int left = 0;
        int right = str.length() - 1;
        while (left <= right) {
            if (!map.containsKey(str.charAt(left))) {
                return false;
            }
            if (!map.containsKey(str.charAt(right))) {
                return false;
            }
            if (map.get(str.charAt(left)) != str.charAt(right)) {
                return false; //这里是判断666这种情况
            }
            left++;
            right--;
        }
        return true;
    }
}
```