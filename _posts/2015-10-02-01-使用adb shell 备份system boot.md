---
layout: post
title: 使用adb shell 备份system boot
date: 2015-10-02
categories: blog
tags: [Android]

---



首先通过df命令查看 boot 和system 分区

```
dd if=/dev/block/mmcblk0p17 of=/media/changyuet/android/system.img    （备份system分区）
dd if=/sdcard/system.img  of=/dev/block/mmcblk0p17  （还原system）
```
