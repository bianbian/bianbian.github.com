---
layout: post
title: Windows 7远程桌面连接很慢怎么办？
category: tech
tags: windows 7, network
---
Windows 7通过远程桌面连接访问windows server 2003速度很慢，用下面的方法，立马解决（改善）了我的问题。

Windows Vista 附带接收窗口自动调谐功能，该功能可为通过网络接收 TCP 数据的程序提高性能。
如果您为 WinHTTP 通信启用接收窗口自动调谐功能，则网络上的数据传输效率可能会更高。但是，在某些情况下，**如果网络使用的路由器和防火墙陈旧老化，且不支持此功能，则数据传输可能会放慢，或者会导致连接中断。**

**如何禁用接收窗口自动调谐功能？**

用管理员权限打开一个cmd窗口,运行以下命令：

	netsh interface tcp set global autotuninglevel=disabled

参考：  
[Description of the Receive Window Auto-Tuning feature for HTTP traffic on Windows Vista-based computers](http://support.microsoft.com/kb/947239)
