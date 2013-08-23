---
layout: post
category: tech
tags: ubuntu, grub4dos
title: Windows7下硬盘安装ubuntu 12.04
---
grub4dos是Windows下硬盘安装linux的不二之选。

## 准备工作 ##
下载[grub4dos 0.44](http://download.gna.org/grub4dos/)和[ubuntu 12.04](http://www.ubuntu.com/download)。

## Windows启动管理器添加grub4dos启动项 ##
打开compmgmt.msc，点击磁盘管理，找到到活动分区(Active Partitioin)。如果活动分区没有盘符，就给它加上盘符。

打开活动分区，把grub4dos文件（grldr grldr.mbr menu.lst）放到根目录，

创建boot.ini，内容如下：

	[boot loader]
	[operating systems]
	c:\grldr.mbr="grub4dos"

前两行不可省略，第三行必须是c:\grldr.mbr="xxx"。

## grub4dos添加ubuntu安装项 ##

打开menu.lst，添加如下内容：

	title install ubuntu 12.04.2
	find --set-root /ubuntu-12.04.2-desktop-i386.iso
	map /ubuntu-12.04.2-desktop-i386.iso (hd32)
	map --hook
	kernel (hd32)/casper/vmlinuz boot=casper iso-scan/filename=/ubuntu-12.04.2-desktop-i386.iso noprompt noeject
	initrd (hd32)/casper/initrd.lz
	boot

/ubuntu-12.04.2-desktop-i386.iso根据实际情况修改。

## 安装ubuntu ##
重启电脑，选择grub4dos，选择install ubuntu 12.04.2，进入Live CD。

打开terminal，输入``sudo umount -l -r -f /isodevice``。然后双击桌面上的图标启动安装程序。详细安装过程可以参照下面的文章：

[Install Ubuntu 12.04.2 LTS](http://www.ubuntu.com/download/desktop/install-desktop-long-term-support)  
[How to Install Ubuntu 12.04 Precise Pangolin](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin#.UhdbcdJmiSp)

参考：  
[Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
