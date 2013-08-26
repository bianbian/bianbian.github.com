--- 
layout: post
title: Raspberry Pi到手
category: tech
tags: 
- raspberry pi
- raspbian
- ttl
---
器材们:

* Raspberry Pi Module B, 6月26号在[e络盟](http://cn.element14.com/)下的定单,本来预计9月到货,后来产能增加,昨天到手了:)
* 亚马逊买的[SanDisk SDHC Class4 8G卡](http://www.amazon.cn/gp/product/B003E7G3PC)
* 魅族充电器UP0508,5V 800mA
* Nokia数据线(micro USB)
* 淘宝买的USB-TTL线

手里有一个VGA显示器,要看视频的话还要买HDMI转VGA线,USB HUB,USB键盘鼠标.好多米...于是没买.

SD卡刷入raspbian, [接上TTL](http://lavalink.com/2012/03/raspberry-pi-serial-interfacing/ "Raspberry Pi serial interfacing"), putty Serial设置为Speed:115200, Flow Control:None(不然会有乱码), 插电,顺利启动.

![putty serial config](http://img.bianbian.me/blog/201209/putty-serial-config.png)

没遇到SD卡不兼容的问题,本来还准备了一个Kingston Class6卡的...

Cheers~
