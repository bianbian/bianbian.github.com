---
layout: post
title: 获取中文linux桌面文件夹的路径
category: tech
tags: linux
---
linux会为桌面用户很“贴心”的在home目录下面创建几个常用文件夹。中文linux创建的是：桌面，文档等；英文linux创建的是Desktop,Documents等。这些文件夹都是实实在在的文件，而不是软链接之类。  
这样在非英文用户在获取桌面文件夹路径时就不能统一地用`~/Desktop`了。

那怎么办呢？先来了解一下这些文件是怎么来的。桌面版的linux有一个工具xdg-user-dirs，它会在用户登陆时根据用户locale创建这些本地化的文件：如果用户locale是en_US就创建"Desktop"；如果 用户locale是zh_CN就创建"桌面"。  
它有两个系统级的配置文件：

	/etc/xdg/user-dirs.defaults
	/etc/xdg/user-dirs.conf

两个用户级的配置文件：

	$(XDG_CONFIG_HOME)/user-dirs.dirs
	$(XDG_CONFIG_HOME)/user-dirs.locale

XDG_CONFIG_HOME默认是~/.config，本地化的文件路径就在user-dirs.dirs中。 
要获取桌面文件夹路径，可以使用下面的命令：

	test -f ${XDG_CONFIG_HOME:-~/.config}/user-dirs.dirs && source ${XDG_CONFIG_HOME:-~/.config}/user-dirs.dirs
	echo ${XDG_DESKTOP_DIR:-$HOME/Desktop}

也可以安装xdg-user-dir工具来获取：

	xdg-user-dir DESKTOP


如果觉得中文文件名不方便，想换成英文的，运行下面命令：

	export LANG=en_US
	xdg-user-dirs-gtk-update

按提示更新，文件夹就更新成英文的了。

参考:

* [xdg-user-dirs](http://freedesktop.org/wiki/Software/xdg-user-dirs/)
* [xdg-user-dir](http://www.unix.com/man-page/all/1/xdg-user-dir/)
* [XDG Base Directory Specification](http://standards.freedesktop.org/basedir-spec/basedir-spec-latest.html)
