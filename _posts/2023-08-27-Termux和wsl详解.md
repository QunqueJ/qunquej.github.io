---
layout:     post
title:      Termux/wsl
subtitle:   在Termux/WSL上安装Linux图形化界面
date:       2023-08-27
author:     QunqueJ
header-img: img/post-bg-cook.jpg
catalog: true
tags:
    - Termux
    - WSL
    - Ubuntu
    - Linux
---

## 前言

官网：https://gitee.com/mo2/linux

https://github.com/2moe/tmoe-linux

使用`Tmoe-linux`可以在 `GNU/Linux、android Termux` 和Windows10 的` linux 子系统(WSL)`上配置 GNU/Linux chroot 或 proot 容器环境，并配置远程桌面、pulseaudio 音频服务和 system。

## 手机 Termux 使用 tmoe-linux 简化操作

### 准备工作

在 [官网](https://termux.dev/en/) 下载并安装 `Termux` 最新版本，并输入以下命令：

#### 切换清华源↓
```	objc
- sed -i 's@^\(deb.*stable main\)$@#\1\ndeb https://mirrors.tuna.tsinghua.edu.cn/termux/apt/termux-main stable main@' $PREFIX/etc/apt/sources.list
```

#### 更新软件包↓
```	objc
- apt update
- apt upgrade
```

### 安装

手机安装`Termux`后获取 2moe 大佬的脚本，按照显示的菜单进行后续安装。

```	objc
- bash -c "$(curl -L git.io/linux.sh)"
- bash -c "$(curl -L l.tmoe.me)"
- bash -c "$(curl -L https://gitee.com/mo2/linux/raw/2/2)"
```

手机没有 root 则选择 proot 容器；
有 root 可选 chroot 容器。（实际上并不推荐给予 Termux root 权限，很危险！）

可选安装 `Debian、Arch、Fedora、Ubuntu、Deepin、Kali` 等发行版。

当然最好还是在自己的电脑上体验完整的的 Linux 系统，arm64 版移植系统体验很糟糕，各种报错😣，Ubuntu、Kali 等发行版都提供 live 镜像，可以试用之后再考虑是否实机安装。顺便强烈推荐 Ventoy ，比 Rufus 等启动盘制作工具更舒服。

## Win10/11 使用 WSL 安装图形化界面

### 准备工作

1、以管理员身份运行powershell，并输入以下命令，然后回车。

```	objc
- dism.exe /online /enable-feature /featurename:Microsoft-windows-Subsystem-Linux /all /norestart
- dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

或者在启用或关闭windows功能中启用“适用于Linux的Windows”和“虚拟机平台”。

2、下载、安装WSL2 Linux内核更新程序包，重启系统后再次以管理员身份运行 powershell ，然后输入以下命令：

```	objc
- wsl --set-default-version 2
```

3、打开Microsoft Store，然后选择您喜欢的Linux发行版。

### 安装

1、打开子系统，然后根据提示更新 WSL2 的 linux 内核。更新完成后，重新打开子系统，然后输入以下命令：

```	objc
- sudo apt update
- sudo apt install -y curl
- bash -c "$(curl -L gitee.com/mo2/linux/raw/2/2)"
```

如果你在国外。请输入：

```	objc
- bash -c "$(curl -L git.io/linux.sh)"
```

输入后进入界面，选择 `Tool`，之后自己安装
