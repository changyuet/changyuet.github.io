---
layout: post
title: 从ota卡刷包recovery-from-boot.p生成recovery.img
date: 2015-09-12
categories: blog
tags: [Android]

---

如果手机官方没有提供线刷包，和无法通过手机里面提取recovery情况下可以尝试提供卡刷包来生成官方recovery.img，当然你的OTA卡刷包里面必须要有boot.img、recovery-from-boot.p、install-recovery.sh三个文件缺一不可，然后利用android applypatch来生成，system/bin/目录下即可。

1、applypatch指令帮助：
```Bash
shell@ha3g:/data/local/tmp $ applypatch
usage: applypatch [-b <bonus-file>] <src-file> <tgt-file> <tgt-sha1> <tgt-size>
[<src-sha1>:<patch> ...]
or applypatch -c <file> [<sha1> ...]
or applypatch -s <bytes>
or applypatch -l
```
2、将applypatch、boot.img、recovery-from-boot.p推送（adb push ）到/data/local/tmp/目录；给予applypatch 755quan

3、打开nstall-recovery.sh文件：
```
#!/system/bin/sh
update_recovery –check-sha1 908410f138130a19caf8fbbc2f2d89496f6caa41 \
–src-sha1 a56291c5b942895ecf64da89e55c5ac444b5a939 \
–tgt-sha1 f44fd8fdc4bc4382fab01f5eb966ee9956b42120 \
–tgt-size 11330560 \
–patch /system/recovery-from-boot.p
```
其中：src-sha1表示recovery-from-boot.p的sha1值；tgt-size表示recovery的大小；tgt-sha1表示recovery的sha1值；

4、生成命令如下：
applypatch <boot文件> <recovery.img tgt-sha1值> <tgt-sized大小> <src-sha1值>:recovery-from-boot.p

如：
```
applypatch boot.img recovery.img f44fd8fdc4bc4382fab01f5eb966ee9956b42120 11330560 a56291c5b942895ecf64da89e55c5ac444b5a939:recovery-from-boot.p
```
