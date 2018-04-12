---
layout: post
title: MIUI适配 patchrom
date: 2015-10-23
categories: blog
tags: [Android]

---

<div>

<br>
<br>同步源码

<br>源码目录创建机型目录

<br>sudo adb kill-server

<br>sudo adb start-server

<br>sudo adb reboot recovery

<br>adb devices

<br>进入机型目录

<br>cd miui

<br>source build/envsetup.sh

<br>cd wa1

<br>手机进入rec

<br>../tools/releasetools/ota_target_from_phone -r

 

<br>编写 makefile

 

<br>然后执行 make workspace

 

<br>然后执行 make firstpatch

</div>
