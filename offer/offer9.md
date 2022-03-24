# 剑指offer系列 - 剑指 Offer II 009. 乘积小于 K 的子数组

## 题目描述
[题目地址](https://leetcode-cn.com/problems/ZVAVXX/)
> 给定一个正整数数组 nums和整数 k ，请找出该数组内乘积小于 k 的连续的子数组的个数。

示例 1:

> 输入: nums = [10,5,2,6], k = 100
> 
> 输出: 8
> 
> 解释: 8 个乘积小于 100 的子数组分别为: [10], [5], [2], [6], [10,5], [5,2], [2,6], [5,2,6]。
> 
> 需要注意的是 [10,5,2] 并不是乘积小于100的子数组。
> 

## 思路

### 遍历 以i结尾的小于k的个数累加

```
    let result = 0;

    for (let i = 0; i < nums.length; i++) {
        let j = i;
        let product = nums[i];
        while (j >= 0 && product < k) {
            result++;
            j--;
            product *= nums[j];
        }
    }

    return result;
```

### 双指针
```
    let l = 0;
    let r = 0;
    let product = 1;
    let result = 0;

    while (r < nums.length) {
        if (nums[r] * product < k) {
            result = result + r - l + 1;
            product *= nums[r];
            r++;
        } else {
            if (l === r) {
                r++;
            } else {
                product /= nums[l];
            }
            l++;
        }
    }

    return result;
```

### 结果
![运行结果](./offer9.png)
