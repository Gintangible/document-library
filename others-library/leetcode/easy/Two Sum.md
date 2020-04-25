# two sum

[leetcode 地址](https://leetcode-cn.com/problems/two-sum/)

题目描述：

给定一个整数数组 nums 和一个目标值 target，请你在该数组中找出和为目标值的那 两个 整数，并返回他们的数组下标。

示例：

```
给定 nums = [2, 7, 11, 15], target = 9

因为 nums[0] + nums[1] = 2 + 7 = 9
所以返回 [0, 1]
```

初始解题方案：

```
var twoSum = function(nums, target) {
    for(let i = 0; i < nums.length - 1; i++) {
        const otherIndex = nums.indexOf(target - nums[i], i  + 1);
        if (otherIndex > -1) {
            return [i, otherIndex];
        }
    }
};
```

执行用时：148 ms 内存消耗：33.7 MB

因为两次查找用的数组，数组查找的时间比较慢。

优化解题方案：

```
var twoSum = function(nums, target) {
    let maps = {};

    for (let i = 0; i < nums.length; i++){
        // 下标为 0。
        if (maps[target - nums[i]] >=0) {
            return [maps[target - nums[i]], i]
        }
        maps[nums[i]] = i;
    }
};
```

执行用时：76 ms 内存消耗：34.6 MB