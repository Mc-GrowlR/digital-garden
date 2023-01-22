# 更换中国源

``` shell
Server = https://mirrors.tuna.tsinghua.edu.cn/archlinux/$repo/os/$arch
Server = http://mirrors.163.com/archlinux/$repo/os/$arch
Server = http://mirrors.aliyun.com/archlinux/$repo/os/$arch
```

# 日常使用常见问题
## 清理空间
``` shell
sudo pacman -Scc
```

## 开机自动挂载NTFS硬盘


### 参考博客
[(99条消息) Manjaro&Arch 自动挂载NTFS分区_UYWOLFER的博客-CSDN博客_arch 自动挂载](https://blog.csdn.net/weixin_43888694/article/details/128260469)

[(99条消息) arch Linux 对NTFS硬盘进行读写操作；开机自动挂载硬盘_archlinux ntfs_印青尧的博客-CSDN博客](https://blog.csdn.net/weixin_43801670/article/details/125105727)

## 检查驱动

``` shell
lspci -v     
```

然后找“kernel driver in use”，没有就是没驱动。

**备注：**

1. 驱动一般都在内核里面，也可以编译成模块，启动后再加载。想nvidia这不开源的，就进不了内核。

2. 内核里面有很多驱动，但是不可能把每个驱动都集成进去，不然内核要爆炸。各种驱动都是选择的主流的集成进去，过时的都编译成模块，自己按需选择。驱动装好不意味着就声音，还要用户空间的库支持，alsa这些，图形应用还有前端设置。算是依赖比较多的容易出问题的。
3. `Monojory`有一个极其方便的功能：mhwd

## 配置邮箱

建议使用雷鸟

与之相关的日历同步问题暂时未解决

## 文件同步备份问题



# 有趣的项目

## 1. ventoyVentoy A new bootable USB solution

**项目地址**：[ventoyVentoy A new bootable USB solution.](https://github.com/ventoy/Ventoy)

**备注**：这个，可以让你引导u盘里面的ios，img，vmdk，vdi，wmi

**预览**：

![[Ventoy.jpg]]

# 软件安装

## 输入法

``` shell
yay -S fcitx5-im fcitx5-chinese-addons
```

## steam

``` shell
yay -S steam
```

安装之后在桌面会在桌面创建快捷方式，点击即可启动。或者直接在终端输入`steam`

首次启动会下载必要文件。注意此时需要翻墙。不然会报网络错误。

## cuda

使用以下命令可以查看系统的显卡驱动情况

``` shell
nvidia-smi
```

在arclinux官网上显示，其开放源中有CUDA和CUDNN驱动环境，可以直接使用pacman进行安装即可:

``` shell
sudo pacman -S cuda cudnn
```

网上还有种解决方法，下载`ubuntu`的`deb`包安装。

**差别**：最新的版本是`12`，而用`aur`源下载的包的版本是`11.8`

## vscode

``` shell
yay -S visual-studio-code-bin
```
> 安装时间：2022-01-11
## QQ

由于腾讯最近更新了QQ Linux 版3.0，因此有两种选择：

1. Linux AppImage版：

[QQ下载界面](https://im.qq.com/linuxqq/index.shtml)

点击下载`AppImage`版。

此版本下载之后，直接就能使用。不过有些功能较之win版还是有所欠缺。

2. wine版

``` shell
yay -S deepin-wine-qq
```
不过我测试有一些BUG：
    - 界面无法操作
    - 输入账号、密码之后无法登陆

## 微信

``` shell
curl https://github.com/canihavesomecoffee.gpg | gpg --import
yay -S lib32-udis86-git
yay -S deepin-wine-wechat --mflags --skipinteg
```

此方法不会出现md5校验错误。

下载之后的微信版本为`3.8.1.26`

**安装成功提示：**

``` shell
============================提示/INFO===============================
* 常见问题及解决(Troubleshoot):
  https://github.com/vufa/deepin-wine-wechat-arch
* 反馈问题(Report issue):
  https://github.com/vufa/deepin-wine-wechat-arch/issues
* 安装包下载(Installation package download):
  https://github.com/vufa/deepin-wine-wechat-arch/releases
====================================================================
deepin-wine-wechat 的可选依赖    noto-fonts-sc: display some Chinese characters
    lib32-nvidia-utils: required for nvidia graphics card
:: 正在运行事务后钩子函数...
(1/4) Arming ConditionNeedsUpdate...
(2/4) Refreshing PackageKit...
(3/4) Updating icon theme caches...
(4/4) Updating the desktop file MIME type cache...
```

## 出现的问题

### aur包安装出现文件md5校验出错

**错误提示：**
``` shell
==> 正在验证 source 文件，使用md5sums...
    com.qq.weixin.deepin_3.4.0.38deepin6_i386.deb ... 通过
    WeChatSetup-3.8.0.41.exe ... 失败
    libldap-2.4-2_2.4.47+dfsg.4-1+eagle_i386.deb ... 通过
    libsasl2-2_2.1.27.1-1+dde_i386.deb ... 通过
    run.sh ... 通过
    reg.patch ... 通过
==> 错误： 一个或多个文件没有通过有效性检查！
    -> 生成时出错: deepin-wine-wechat
```

**解决方法：**

打开`/home/用户名/.cache/yay/软件包名/`

``` shell
vim PKGBUILD
```

将`md5sums`中用单引号阔起来的部分换成`SKIP`，注意一定要大写。

**参考网站：**

1. 如何修改：[从deepin迁移到其他Linux  Xpanx](https://xpanx.com/3148.html)

2. 修改示范：[aur报错（错误：一个或多个文件没有通过有效性检查）](https://blog.csdn.net/qq_37284020/article/details/103991649)

### 界面语言

安装之后默认的语言是英文。

可在设置里面调整：
> `settings` => `general` => `language` => `简体中文`
> 随后在弹出的界面里点击`OK`即可。
> 点击`OK`之后微信会重新启动，这是就会看到界面已经改成了中文。

### 解决缺少包问题

有以下两种解决方法：

1. github

项目地址：[deepin-udis86](https://github.com/JohnMasoner/deepin-udis86)

``` shell
git clone https://github.com/JohnMasoner/deepin-udis86.git
cd deepin-udis86/
makepkg -i
```

2. multilib

``` shell
sudo vim /etc/pacman.conf
```

找到下面的区域，将其中的`[multilib]`两行取消注释

``` yaml
# If you want to run 32 bit applications on your x86_64 system,
# enable the multilib repositories as required here.

#[multilib-testing]
#Include = /etc/pacman.d/mirrorlist

[multilib]
Include = /etc/pacman.d/mirrorlist
```

然后`pacman -Sy`更新即可。

不过，开启`multilib`之后操作系统会被污染，因为现代操作系统默认是64位的。但是使用wine的话要使用lib32，如果管理不当后面会产生一大堆的依赖问题。
