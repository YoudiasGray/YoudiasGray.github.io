---
title: dvorak键位输入
date: 2019-08-18 18:31:41
tags:
    - dvorak
---

# Dvorak简介

一种键盘布局，相对于常见的QWERTY键位，据说效率更高。

详细介绍参考百度：https://baike.baidu.com/item/Dvorak%E9%94%AE%E7%9B%98/177639?fr=aladdin

键盘布局如下：

![Dvorak键位 理性的正向革新终遭失败 ](https://article-fd.zol-img.com.cn/t_s640x2000/g5/M00/0C/01/ChMkJ1p4EcWIcN5IAADBoGvXxk0AAkrAQOorMsAAMG4618.jpg)

# 使用

## 英文输入

windows自带dvorak布局，切换输入法后直接使用即可。

## 中文输入

输入法可以修改所用的键盘布局，之前做法是额外安装一个谷歌输入法，注册表里面修改，后来的windows版本该方法无效。

不过可以通过Autohotkey间接实现，通过将输入映射，实现在普通键盘上进行dvorak输入。

映射脚本如下：

```
-::[
=::]
q::'
w::,
e::.
r::p
t::y
y::f
u::g
i::c
o::r
p::l
[::/
]::=
;a::a
s::o
d::e
f::u
g::i
h::d
j::h
k::t
l::n
`;::s
'::-
z::`;
x::q
c::j
v::k
b::x
n::b
;m::m
,::w
.::v
/::z
```



# 其他

使用WhatPulse记录一段时间后，dvorak布局下的输入确实更集中主键位上，但是需要时间来熟悉适应，QWERTY下越熟练，新键位用起来越别扭。利用空闲时间练习熟悉，相信是值得的。