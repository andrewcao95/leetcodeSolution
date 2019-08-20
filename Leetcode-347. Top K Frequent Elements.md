## Solution
- step1.显然，为了找出数组中出现频次最多的前k个元素，首先，我们需要分别统计出数组中各个元素出现的频次，很容易想到哈希表，Java中提供了HashMap类，它实现了Map接口，HashMap是一个泛型类（HashMap<key,value>），可以用来存储键/值对，为了统计数组个元素的频次，我们可以把元素数值作为“键”，对应元素出现的次数作为“值”，如此，我们只需要对数组进行一次遍历就可以得到一张包含不同数组元素和对应出现频次的“映射表”。

- step2.由于我们关心的是出现频次最多的前k个元素，因此，得到频次统计“映射表”之后，我们需要根据频次对映射表中的键/值对进行排序。

- step3. 映射表中键（数据元素）和值（该数据元素出现的频次）是一一对应的，我们在按值进行排序的同时需要记录其对应的元素，鉴于此，我们可以采用“桶排序”的思想。由于我们是按数据元素出现的频次进行排序的，那么“桶”的数量范围是可以确定的——桶的数量小于等于给定数组元素的个数。编号为i的桶用于存放数组中出现频次为i的元素——即编号为i的桶存放“映射表”中“值”等于i的“键”。

- step4. 排序完成后，编号大的桶中元素出现的频次高，因此，我们“逆序”(先取桶编号大的桶的元素)获取桶中数据，直到获取数据的个数等于k，我们将当前桶的元素取尽（同一个桶中元素出现的频次相等）,然后停止取数据，完成！

```java
public List<Integer> topKFrequent(int[] nums, int k) {
    HashMap<Integer, Integer> map = new HashMap<>();
    for (int num : nums) {
        map.put(num, map.getOrDefault(num, 0) + 1);
    }
    List<Integer>[] bucket = new List[nums.length + 1];
    for (int num : map.keySet()) {
        int freq = map.get(num);
        if (bucket[freq] == null) {
            bucket[freq] = new ArrayList<>();
        }
        bucket[freq].add(num);
    }
    
    List<Integer> res = new ArrayList<>();
    for (int i = bucket.length - 1; i >= 0 && res.size() < k; i--) {
        if (bucket[i] != null) {
            res.addAll(bucket[i]);
        }
    }
    return res;
}
```