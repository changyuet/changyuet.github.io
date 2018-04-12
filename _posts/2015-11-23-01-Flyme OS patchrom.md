---
layout: post
title: Flyme OS patchrom
date: 2015-11-23
categories: blog
tags: [Android]

---

## 1 重启进recovery拉包或者手动放入ota包
* adb reboot recovery
* cd /media/changyuet/android/flyme

## 初始化环境
* . build/envsetup.sh

## 建立文件夹开始
* mkdir -p devices/CP8297_T01
* cd devices/CP8297_T01
* flyme config
* flyme newproject
* flyme patchall
