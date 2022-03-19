# 剑指offer系列 - 剑指 Offer II 002. 二进制加法

## 题目描述
[题目地址](https://leetcode-cn.com/problems/JFETK5/)
> 给定两个 01 字符串 a 和 b ，请计算它们的和，并以二进制字符串的形式输出。
> 
> 输入为 非空 字符串且只包含数字 1 和 0。

示例 1:

> 输入: a = "11", b = "10"
> 
> 输出: "101"

示例 2:
> 输入: a = "1010", b = "1011"
> 
> 输出: "10101"


## 思路

### 按位相加记录进位

补全`a`、`b`长度不一致

```
    let len = Math.max(a.length, b.length);
    // 补全a、b长度不一致
    if (a.length < len) {
        a = Array(len - a.length).fill(0).join('') + a;
    }
    if (b.length < len) {
        b = Array(len - b.length).fill(0).join('') + b;
    }
    let add = 0;
    let result = '';
    for (let i = len - 1; i >=0; i--) {
        let sum = +a[i] + +b[i] + add;
        add = Math.floor(sum / 2);
        result = sum % 2 + result;
    }

    return add ? add + result : result;
```
双指针 无需补全
```
    let aIndex = a.length - 1;
    let bIndex = b.length - 1;
    let add = 0;
    let result = '';

    while (aIndex >= 0 || bIndex >= 0) {
        let sum = +(a[aIndex] || 0) + +(b[bIndex] || 0) + add;
        add = Math.floor(sum / 2);
        result = sum % 2 + result;
        aIndex--;
        bIndex--;
    }

    return add ? add + result : result;
```

### 位运算

[官方题解](https://leetcode-cn.com/problems/JFETK5/solution/er-jin-zhi-jia-fa-by-leetcode-solution-fa6t/)
官方有一个python例子，思路非常不错，实现一个js版本
```
    a = BigInt('0b' + a);
    b = BigInt('0b' + b);

    // return (a + b).toString(2)

    while (b) {
        let temp = a ^ b;
        b = (a & b) << BigInt(1);
        a = temp;
    }
    return a.toString(2);
```

### 结果
![运行结果](offer2.png)
