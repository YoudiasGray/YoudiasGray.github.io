---
title: LeetCode
date: 2019-07-27 21:03:07
tags:
	- leetcode

---

# LeetCode解题记录

## 起因

确定一个目标，每天AC一道题，看能做多久。

## 解题记录

### 202 计数质数

### 链接：https://leetcode-cn.com/problems/count-primes/

### 题目：

统计所有小于非负整数 *n* 的质数的数量。

**示例:**

```
输入: 10
输出: 4
解释: 小于 10 的质数一共有 4 个, 它们是 2, 3, 5, 7 。
```

### 分析：

1 编写函数实现判断是否是素数

2 统计范围内素数个数

### AC代码：

```c++
class Solution {
public:
    int countPrimes(int n) {
        int ret=0;
        for(int i=2;i<n;i++)
        {
            if(IsPrime(i))
            {
                ret++;
            }
        }
        return ret;        
    }
    bool IsPrime(int input)
    {
        bool ret=true;
        for(int i=2;i*i<=input;i++)
        {
            if(input%i == 0)
            {
                return false;
            }
        }
        return ret;
    }
};
```



