---
layout: post
title: windows7 使用硬盘安装 linux的教程笔记
date: 2015-03-02
categories: blog
tags: [Linux]

---


## 前期准备linux的ISO镜像文件 
easybcd软件
 图文教程开始
 注意 此教程适合win7 vista系统 如果是XP系统  需要安装grub2 软件 来代替easybcd

* 1 打开你下载的linux iso文件 找到casper文件夹 复制initrd.lz 和vmlinuz 2个文件 以及iso镜像到C盘 
   <img class="shadow" src="/images/posts/2015-03-02/1.png" width="291" high="165">

* 2 打开easybcd这个软件 选择添加新条目 然后选择 neogrub 然后选择 配置
<img class="shadow" src="/images/posts/2015-03-02/2.jpg" width="588" high="471"> 

* 3 然后在 弹出的menu.lst 启动列表 输入

```
title Install linuxmint  #名字随意
root (hd0,0)
kernel (hd0,0)/vmlinuz boot=casper iso-scan/filename=/linuxmint-16-kde-dvd-64bit.iso locale=zh_CN.UTF-8
initrd (hd0,0)/initrd.lz
```
如图

<img class="shadow" src="/images/posts/2015-03-02/3.png" width="948" high="120">

注意 filename=/ 后面你的ISO文件名   /linuxmint-16-kde-dvd-64bit.iso  这个是我ISO文件名 你需要换成你的        (HD0,0)代表第一块硬盘 第一个分区

然后保存 重启

你会看到windows启动项下面多了一个 neo的启动项 
选择它

进入

<img class="shadow" src="/images/posts/2015-03-02/4.jpg" width="960" high="712">

然后回车  顺利的话 就开始加载镜像文件

进入安装界面

<img class="shadow" src="/images/posts/2015-03-02/5.jpg" width="960" high="712">
