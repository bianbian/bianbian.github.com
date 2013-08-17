---
layout: post
category: tech
tags: grub4dos, ubuntu
title: Windows7下用grub4dos安装ubuntu 12.04
---
grub4dos是Windows下安装linux的一个二的不二之选。

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
提取ubuntu-12.04.2-desktop-i386.iso中/casper/目录下vmlinuz initrd.gz放到活动分区根目录。

打开menu.lst，添加如下内容：

	title install ubuntu 12.04.2
	root (hd0,0)
	kernel /vmlinuz boot=casper iso-scan/filename=/ubuntu-12.04.2-desktop-i386.iso ro quiet splash
	initrd /initrd.lz
	boot

(hd0,0)和/ubuntu-12.04.2-desktop-i386.iso根据自己硬盘分区情况和文件路径进行修改。

## 安装ubuntu ##
重启电脑，选择grub4dos，选择install ubuntu 12.04.2进行安装。
