---
layout: post
category: tach
tags: ubuntu, apt-get
title: ubuntu更新卡在Wating for headers
---
在ubuntu上安装软件，先运行``sudo apt-get update``，顺利运行，速度还可以。

但是运行``sudo apt-get install xxx``的时候一直停在"Wating for headers"阶段，然后连接超时，安装失败。

网上搜了一下，原来是apt的cache惹的祸，删除``/vat/cache/apt/archives/partial/``下面的文件，再运行安装命令就可以了。无比顺滑:D

参考：
- [解决Ubuntu/Debian卡在Waiting for headers的问题](http://yynotes.net/ubuntu-debian-waiting-for-headers/)
- [E: Archive directory /var/cache/apt/archives/partial is missing Error and Solution](http://www.cyberciti.biz/faq/debian-ubuntu-linux-earchive-directory-varcacheaptarchivespartial-ismissing/)
