# 问题描述

给定一个整数数组，返回相加得到一个特定的目标的两个数字的索引。

假设每个输入都只有一个解决方案，并确保不会两次使用相同的元素。

比如：

> ```
> Given nums = [2, 7, 11, 15], target = 9,
>
> Because nums[0] + nums[1] = 2 + 7 = 9,
> return [0, 1].
> ```

# 方案v1.0

比较暴力的一种方式，穷举法。时间复杂度为O(n^2)，空间复杂度为O(1)。

```
class Solution {
    public int[] twoSum(int[] nums, int target) {
        int[] result = new int[2];
        for (int i = 0; i < nums.length - 1; i++) {
            for (int j = nums.length - 1; j > i; j--) {
                if (nums[i] + nums[j] == target) {
                    result[0] = i;
                    result[1] = j;
                    return result;
                }
            }
        }
        return result;
    }
}
```

# 方案v2.0

从另一个角度思考，我们不判断是否存在两数相加等于特定值，而是去判断特定值减去当前元素的差值(补码)是否存在于数组中。因为只有一层循环，所以时间复杂度为O(n)，但是因为我们增加了额外的空间，所以空间复杂度为O(n)。

```
class Solution {
    int[] result = new int[2];
    Map<Integer, Integer> complements = new HashMap<>();
    for (int i = 0; i < nums.length; i++) {
        int complement = target - nums[i];
        if (complements.containsKey(complement)) {
            result[0] = complements.get(complement);
            result[1] = i;
            return result;
        }
        complements.put(nums[i], i);
    }
    return result;
}
```