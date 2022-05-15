# 633. 平方数之和

## 题目描述
[题目地址](https://leetcode.cn/problems/sum-of-square-numbers/)
> 给定一个非负整数 c ，你要判断是否存在两个整数 a 和 b，使得 a2 + b2 = c 。

示例 1:

> 输入：c = 5
> 
> 输出：true
> 
> 解释：1 * 1 + 2 * 2 = 5

示例 2:
> 输入：c = 3
> 
> 输出：false


## 思路

### 双指针
```
    let left = 0;
    let right = Math.ceil(Math.sqrt(c));

    while (left <= right) {
        const result = left**2 + right**2;
        if (result < c) {
            left++;
        } else if (result > c) {
            right--;
        } else {
            return true;
        }
    }

    return false;
```


### 结果
![运行结果](leetcode633.png)
