## Solution1
```java
class Solution {
    public List<List<Integer>> kSmallestPairs(int[] nums1, int[] nums2, int k) {
        List<List<Integer>> res = new ArrayList<>();
        if (nums1.length == 0 || nums2.length == 0 || k == 0) {
            return res;
        }
        PriorityQueue<List<Integer>> pq = new PriorityQueue<>((a,b) -> (a.get(0) + a.get(1) - b.get(0) - b.get(1)));
        for (int num1 : nums1) {
            for (int num2 : nums2) {
                List<Integer> temp = new ArrayList<>();
                temp.add(num1);
                temp.add(num2);
                pq.add(temp);
            }
        }

        while (!pq.isEmpty() && k > 0) {
            res.add(pq.poll());
            k--;
        }
        return res;
    }
}
```

## Solution2
- time: O(klogk)/O(nlogk)
- space: O(k)

```java
class Solution {
    public List<List<Integer>> kSmallestPairs(int[] nums1, int[] nums2, int k) {
        List<List<Integer>> res = new ArrayList<>();
        if (nums1.length == 0 || nums2.length == 0 || k == 0) {
            return res;
        }
        PriorityQueue<List<Integer>> pq = new PriorityQueue<>((a,b) -> (a.get(0) + a.get(1) - b.get(0) - b.get(1)));

        for (int i = 0; i < k && i < nums1.length; i++) {
            List<Integer> temp = new ArrayList<>();
            temp.add(nums1[i]);
            temp.add(nums2[0]);
            temp.add(0);
            pq.offer(temp);
        }

        while (!pq.isEmpty() && k-- > 0) {
            List<Integer> cur = pq.poll();
            List<Integer> temp = new ArrayList<>();
            temp.add(cur.get(0));
            temp.add(cur.get(1));
            res.add(temp);

            if (cur.get(2) == nums2.length - 1) continue;

            List<Integer> newTemp = new ArrayList<>();
            newTemp.add(cur.get(0));
            newTemp.add(nums2[cur.get(2) + 1]);
            newTemp.add(cur.get(2) + 1);
            pq.offer(newTemp);
            
        }
        return res;
    }
}
```