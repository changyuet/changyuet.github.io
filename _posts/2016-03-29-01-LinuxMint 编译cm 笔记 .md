---
layout: post
title: LinuxMint 编译cm 笔记 
date: 2016-03-29
categories: blog
tags: [Android]

---

## LinuxMint 编译cm 笔记 

### 安装软件
```
sudo apt-get install git-core gnupg flex bison gperf libsdl1.2-dev libesd0-dev libwxgtk2.8-dev squashfs-tools build-essential zip curl libncurses5-dev zlib1g-dev openjdk-7-jdk pngcrush schedtool libxml2 libxml2-utils xsltproc lzop libc6-dev schedtool g++-multilib lib32z1-dev lib32ncurses5-dev lib32readline-gplv2-dev gcc-multilib maven tmux screen w3m ncftp ccache
```

### 安装repo
```
mkdir ~/bin
git clone git://aosp.tuna.tsinghua.edu.cn/android/git-repo.git/
cp git-repo/repo ~/bin/
```
### 设置环境
```
gedit ~/.bashrc
```

```
alias repo="~/bin/repo"
export PATH=$PATH:/media/changyuet/android/CM12.1/out/host/linux-x86/bin
export ANDROID_PRODUCT_OUT=/media/changyuet/android/CM12.1/out/target/product/generic
export USE_CCACHE=1
export CCACHE_DIR=/media/changyuet/cache/ccache
```

```
source ~/.bashrc 
```

### 同步源码
```
cd /media/changyuet/android/
mkdir CM12.1
cd CM12.1
repo init -u https://github.com/CyanogenMod/android.git -b cm-12.1
repo sync --no-clone-bundle -c -j4
```

### 编译
```
. build/envsetup.sh
prebuilts/misc/linux-x86/ccache/ccache -M 50G
brunch xxx
or
lunch
make -j8 otapackage
```
