# 524. 通过删除字母匹配到字典里最长单词

## 题目描述
[题目地址](https://leetcode.cn/problems/longest-word-in-dictionary-through-deleting/)
> 给你一个字符串 s 和一个字符串数组 dictionary ，找出并返回 dictionary 中最长的字符串，该字符串可以通过删除 s 中的某些字符得到。
> 
> 如果答案不止一个，返回长度最长且字母序最小的字符串。如果答案不存在，则返回空字符串。


示例 1:

> 输入：s = "abpcplea", dictionary = ["ale","apple","monkey","plea"]
> 
> 输出："apple"

示例 2:
> 输入：s = "abpcplea", dictionary = ["a","b","c"]
> 
> 输出："a"


## 思路

### 双指针
```
    const isGood = (w) => {
        let left = 0;
        let right = 0;

        while (right < w.length && left < s.length) {
            if (s[left] === w[right]) {
                left++;
                right++;
            } else {
                left++;
            }
        }

        return right === w.length
    }

    let len = 0;
    let result = '';

    for (let i = 0; i < dictionary.length; i++) {
        const word = dictionary[i];
        
        if (isGood(word)) {
            if (word.length > len) {
                result = word;
                len = word.length;
            } else if (word.length === len){
                result = word < result ? word : result;
            }
        }
    }

    return result;
```


### 结果
![运行结果](leetcode524.png)
