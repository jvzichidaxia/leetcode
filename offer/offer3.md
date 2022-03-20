# 剑指offer系列 - 剑指 Offer II 003. 前 n 个数字二进制中 1 的个数

## 题目描述
[题目地址](https://leetcode-cn.com/problems/w3tCBm/)
> 给定一个非负整数 n ，请计算 0 到 n 之间的每个数字的二进制表示中 1 的个数，并输出一个数组。


示例 1:

> 输入: n = 2
> 
> 输出: [0,1,1]
> 
> 解释: 
> 
> 0 --> 0
> 
> 1 --> 1
> 
> 2 --> 10

## 思路

### 动态规划

```
    // dp[i] = dp[i >> 1] + 1 or 0
    let dp = Array(n + 1).fill(0);

    for (let i = 1; i <= n; i++) {
        dp[i] = i % 2 === 0 ? dp[i >> 1] : (dp[i >> 1] + 1);
    }

    return dp;
```

### 结果
![运行结果](offer3.png)
