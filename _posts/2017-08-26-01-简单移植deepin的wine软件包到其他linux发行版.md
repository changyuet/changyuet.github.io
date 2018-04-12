---
layout: post
title: 简单移植deepin的wine软件包到其他linux发行版
date: 2017-08-26
categories: blog
tags: [Linux]

---

## 简单移植deepin的wine软件包到其他linux发行版

* 因为是deepin的软件包所以难免会有一些依赖问题，我们只需要去掉这些依赖就可以安装了。所以我们需要对软件包进行修改。但由于依赖问题，所以部分软件并不能完美运行。

### 1.安装dpkg 
  这个软件包估计都是安装过得 
  要是没有安装的可以通过指令或新立得安装 
  执行代码 
```
sudo apt-get install dpkg
```
### 2.修改deepin的wine软件包

* a.获取deepin的wine软件包，可以通过一下网址得到。（请选择其中wine的软件包，其他的可能是deepin下的其他软件包
      [深度软件仓库app](http://packages.deepin.com/deepin/pool/non-free/a/ "悬停显示")  
      [深度软件仓库deepin](http://packages.deepin.com/deepin/pool/non-free/d/ "悬停显示")

* b.选择一个工作目录（随便一个文件夹就行），将wine的软件包放进去，例如此软件包的名字为wine.deb

* c.创建软件包目录 
在此工作目录下打开终端（或直接cd到此工作目录下）运行
```
mkdir -p extract/DEBIAN
```
 

* d.解压wine软件包
```
dpkg-deb -x wine.deb extract/
dpkg-deb -e wine.deb extract/DEBIAN
```
* e.去掉依赖  
 　　打开extract/DEBIAN/control，找到Depends: 去掉不能安装通过的一些依赖，一般只留下包含crossover即可

* f.重新打包 
 建立一个软件包生成目录
```
mkdir build
```
* 重新打包为deb
```
dpkg-deb -b extract/ build/
```

* g.安装
 在build目录下会看到新生成的wine软件包，安装即可。
 然后在crossover中会看到这个容器，运行里面的软件即可
