---
layout: post
title: 新虚拟机里的eth1
category: tech
tags:
- linux
- ubuntu
---
环境:Ubuntu 12.04.2 LTS

用virtual box新建虚拟机，使用之前创建的vdi文件。  
不能联网。``ifconfig``查看，eth0不见了，有一个eth1。eth1没有网络连接。

原因是原虚拟机文件里面保存了网卡eth0信息，新虚拟机分配的网卡命名eth1。而``/etc/network/interfaces``只有eth0的配置信息,没有eth1。  
删除网卡信息后重启，让os重新分配网卡编号,就能联网了。

	sudo rm /etc/udev/rules.d/70-persistent-net.rules
	sudo reboot

参考

* [Cloning Ubuntu Server 7.10 on VMware ESX](http://ephemeralvalue.com/2008/02/18/cloning-ubuntu-server-710-on-vmware-esx/)
