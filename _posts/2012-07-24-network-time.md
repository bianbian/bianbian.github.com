--- 
layout: post
title: Linux网络对时
catagory: tech
tags: 
- linux
- raspberry pi
- raspbian
- ntp
---
rpi这板子没有RTC,所以网络对时是个不错的选择,或者自己加RTC模块...

	sudo apt-get install ntpdate

安装完之后就会自动对时,date一下看是否对准了:)  
默认的对时服务器是debian.pool.ntp.org,国内可能有点延迟,打开配置文件

	sudo vi /etc/ntp.conf

把国内/亚洲/宝岛的对时服务器加上去

	server cn.pool.ntp.org   iburst
	server asia.pool.ntp.org iburst
	server tw.pool.ntp.org   iburst

因为不知道这些组里都有几台server,所以没有加0.cn.pool.ntp.org这样的条目,iburst的意思是10秒对时一次.
