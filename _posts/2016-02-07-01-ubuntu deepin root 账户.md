---
layout: post
title: ubuntu deepin root 账户
date: 2016-02-07
categories: blog
tags: [Linux]

---

<br> 非常简单，只需要重新设置下密码即可。下面是设置的方法

```
me@ubuntu:~$ sudo passwd 
密码：
输入新的 UNIX 密码：
重新输入新的 UNIX 密码
passwd：已成功更新密码 
me@ubuntu:~$ su 
密码：<--输入重置的新密码 
```
