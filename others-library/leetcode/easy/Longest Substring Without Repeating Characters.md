# Longest Substring Without Repeating Characters

[leetcode 地址](https://leetcode-cn.com/problems/longest-substring-without-repeating-characters/)

题目描述：

给定一个字符串，请你找出其中不含有重复字符的 最长子串 的长度。

示例：

```
输入: "abcabcbb"
输出: 3 
解释: 因为无重复字符的最长子串是 "abc"，所以其长度为 3。
```

解题方案：

```
var lengthOfLongestSubstring = function(str) {
    const len = str.length;

    if (!len) return 0;

    let tmpStr = '',
        left = 0;
        maxLen = 0;

    for (let i = 0; i < len; i++) {
        if (tmpStr.indexOf(str[i]) > -1) {
            left += str.slice(left, i).indexOf(str[i]) + 1;
            continue;
        }

        tmpStr = str.substring(left, i + 1);
        maxLen = Math.max(maxLen, tmpStr.length)
    }
    
    return maxLen;
};
```