# 剑指offer系列 - 剑指 Offer II 008. 和大于等于 target 的最短子数组

## 题目描述
[题目地址](https://leetcode-cn.com/problems/2VG8Kg/)
> 给定一个含有 n 个正整数的数组和一个正整数 target 。
> 
> 找出该数组中满足其和 ≥ target 的长度最小的 连续子数组 [numsl, numsl+1, ..., numsr-1, numsr] ，并返回其长度。如果不存在符合条件的子数组，返回 0 。
> 

示例 1:

> 输入：target = 7, nums = [2,3,1,2,4,3]
> 
> 输出：2
> 
> 解释：子数组 [4,3] 是该条件下的长度最小的子数组。
> 

## 思路

### 双指针
```
    let l = 0;
    let r = -1;
    let sum = 0;
    let result = nums.length;
    let flag = false;

    while (r < nums.length) {
        if (sum < target) {
            r++;
            if (r === nums.length) {
                break;
            }
            sum += nums[r];
        } else {
            result = Math.min(result, r - l + 1);
            sum -= nums[l];
            l++;
            flag = true;
        }
    }

    return flag ? result : 0;
```

### 结果
![运行结果](./offer8.png)
