---
layout: post
category: tech
tags: linux, background
title: linux后台进程
---
启动一个后台进程：``nohup command &``

把前台进程暂停并切换到后台：``Ctrl + z``

查看后台进程：``jobs``

让后台暂停的进程恢复执行：``bg &n``

把后台进程切换到前台：``fg &n``

参考：  
[Linux 技巧：让进程在后台可靠运行的几种方法](http://www.ibm.com/developerworks/cn/linux/l-cn-nohup/)
