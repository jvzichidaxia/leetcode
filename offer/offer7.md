# 剑指offer系列 - 剑指 Offer II 007. 数组中和为 0 的三个数

## 题目描述
[题目地址](https://leetcode-cn.com/problems/1fGaJU/)
> 给定一个包含 n 个整数的数组 nums，判断 nums 中是否存在三个元素 a ，b ，c ，使得 a + b + c = 0 ？请找出所有和为 0 且 不重复 的三元组。

示例 1:

> 输入：nums = [-1,0,1,2,-1,-4]
> 
> 输出：[[-1,-1,2],[-1,0,1]]

示例 1:

> 输入：nums = []
> 
> 输出：[]
> 
## 思路

### 双指针 注意过滤重复

```
    let sortNum = nums.sort((a, b) => a - b);
    let result = []

    for (let i = 0; i < sortNum.length - 2; i++) {
        if (i > 0 && sortNum[i] === sortNum[i - 1]) {
            continue;
        }
        let l = i + 1;
        let r = sortNum.length - 1;
        let target = -sortNum[i];

        while (l < r) {
            if (sortNum[l] + sortNum[r] < target) {
                l++;
            } else if (sortNum[l] + sortNum[r] > target) {
                r--;
            } else {
                result.push([sortNum[i], sortNum[l], sortNum[r]]);
                while(sortNum[r - 1] === sortNum[r]) {
                    r--;
                }
                r--;
            }
        }
    }

    return result
```

### 结果
![运行结果](offer7.png)
