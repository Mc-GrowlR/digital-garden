---
title: 
created: 2022-08-18 12:49
uid: 202208181249
aliases: []
tags: []
from: 
editflag: 0
---

# 缘由

一个月前淘到了一块三星平板，平常的用途都是打开百度网盘看看课程啥的，有一天群内有位大佬展示了它的平板，上面跑着 Linux，一下再把我吸引了。加了大佬的好友，经过一番折腾，踩了不少坑，期间经历了 10 天左右。

主要是三星平板系统的特殊性：安装 Linux 后，无法通过 SSH 连接（juiceSSH 连接显式 1005 错误），这是因为平板系统默认开启 `SeLinux` 这让我废了不少时间。期间试过了 Linuxdeploy，也试过 Termux 通过 Tmoe 框架安装，也刷了好几遍系统，都无济于事，大佬跟我说是 `SeLinux` 的锅。但是我不会解决...

终于，在我将系统刷成了 LineageOS  14.1 （安卓版本 7.1.2）时，在设置里关于系统中看到了这一项：SeLinux 状态执行中
![](https://growlr-center-blog-image.oss-cn-beijing.aliyuncs.com/image/20220818115555.png)
这打开了我的解决思路，经过一番折腾，终于在平板成功抛跑起了 Linux 系统，并能通过 SSH 连接。

# 安装步骤

前提：机器已经`root`

## 0. 设置 SELinux

此步重中之重，如果你的系统没有相关选项可以跳过这步。

教程地址：[关闭开启安卓内核selinux状态（附工具）_评测资讯_奇兔rom市场](http://rom.7to.cn/newsdetail/17252)

安装安卓终端模拟器：[Android 终端模拟器 | F-Droid - Free and Open Source Android App Repository](https://f-droid.org/zh_Hans/packages/jackpal.androidterm/)

查看 SELinux 状态

``` shell
getenforce   
```

查看当前 Selinux 功能是 `permissive`(关闭)还是 `enforce`(打开)的

在终端中输入以下命令：

``` shell
su
```
提权

```shell
setenforce 0
```
临时关闭 SELinux

效果：
![](https://growlr-center-blog-image.oss-cn-beijing.aliyuncs.com/image/Screenshot_20220818-121652.png)

此时即可开始安装工作。

## 1. 安装 Linuxdeploy

Linuxdeploy下载地址：[Release Linux Deploy 2.6.0 · meefik/linuxdeploy · GitHub](https://github.com/meefik/linuxdeploy/releases/tag/2.6.0)

下载最新版本（2.60）安装到平板上安装即可。

## 2. 系统安装配置
安装完成后，点击右上角的设置，配置系统安装设置环境。
![](https://growlr-center-blog-image.oss-cn-beijing.aliyuncs.com/image/20220818120344.png)

照着安装即可。用户名和密码自己想一个。

注意源地址填写：
```
https://mirrors.ustc.edu.cn/kali/
```


![](https://growlr-center-blog-image.oss-cn-beijing.aliyuncs.com/image/Screenshot_20220818-120551.png)
![](https://growlr-center-blog-image.oss-cn-beijing.aliyuncs.com/image/Screenshot_20220818-120649.png)
![](https://growlr-center-blog-image.oss-cn-beijing.aliyuncs.com/image/Screenshot_20220818-120703.png)

## 3. 配置软件运行策略

![](https://growlr-center-blog-image.oss-cn-beijing.aliyuncs.com/image/20220818121937.png)

点击左上角，在弹出的选项中点击【设置】
![](https://growlr-center-blog-image.oss-cn-beijing.aliyuncs.com/image/Screenshot_20220818-122037.png)

将【锁定 WiFi】和【CPU 唤醒】勾上即可。

## 4.  安装系统

点击右上角的三个点。

在弹出来的选项中点击【安装】
![](https://growlr-center-blog-image.oss-cn-beijing.aliyuncs.com/image/Screenshot_20220818-122310.png)


点击安装后，软件会要求 root 权限，允许即可。

出现 `<<<deploy` 即安装成功

## 5. 通过 SSH 连接系统

下载 `JuiceSSH` ，下载地址：[JuiceSSH - Free SSH client for Android](https://www.juicessh.com/changelog)

如果你在这款平板上刷的是安卓 10 系统，安装最新版即可。

但我现在使用的安卓 7 系统，在安装最新版本时会出现软件包解析错误的问题。这时就要挑旧版本安装了。我安装的版本是 `2.1.4`

打开 `JUiceSSH` ：

点击右上角的小闪电，打开快速连接：

![](https://growlr-center-blog-image.oss-cn-beijing.aliyuncs.com/image/20220818123822.png)

![](https://growlr-center-blog-image.oss-cn-beijing.aliyuncs.com/image/20220818123852.png)

输入：
```
刚才填写的用户名@127.0.0.1
```

![](https://growlr-center-blog-image.oss-cn-beijing.aliyuncs.com/image/20220818124155.png)

输入密码：

![](https://growlr-center-blog-image.oss-cn-beijing.aliyuncs.com/image/20220818124215.png)

连接成功：
![](https://growlr-center-blog-image.oss-cn-beijing.aliyuncs.com/image/20220818124248.png)

# 常见问题：

## 是否要安装 busybox

在这台机器上不用，因为系统安装完成后就内置命令。

我没有安装 busybox 也能成功安装 Linux 系统

# 参考
[linuxdeploy自动化配置_百口可乐__的博客-CSDN博客](https://blog.csdn.net/m0_60352504/article/details/120464737)