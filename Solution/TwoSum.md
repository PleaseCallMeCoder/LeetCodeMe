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

